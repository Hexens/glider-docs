---
description: Turning a single incident into a scalable detection workflow
icon: '1'
cover: ../.gitbook/assets/Frame 1.png
coverY: 0
---

# Hunting Governance Delegation Bugs with Glider

#### 0) Overview <a href="#id-0-overview" id="id-0-overview"></a>

This write-up explains how you can actually use Glider to turn a concrete finding into a repeatable query. The running example is a Nouns governance issue where delegation to the **zero address** interacts badly with vote-moving helpers.

The main idea is straightforward: once a bug is clearly understood, its “shape” can be encoded into a query. Glider then makes it possible to scan at scale and identify the same issue in multiple codebases, while filtering down to reportable results with manageable false positives.

**The Glider feature covered in this article**

Targets: `Contracts()`, `Functions()` Filters: `.with_signature(...)`, `.with_name(...)`, `.with_callee_names([...])` Execution and inspection: `.exec()`, `.source_code()`, `.get_contract()`

***

***

#### 1) Research phase <a href="#id-1-research-phase" id="id-1-research-phase"></a>

To start off we need some idea that we can turn into a query and result in actual reportable bugs. As a bug bounty hunter, you have a portfolio of previous findings that you can use. For example, I have gone through all of my findings on bug bounty platforms, as well as audits to identify patterns in bug findings. Some of it will be more specific and unique to the codebase, some of it can be generalized more, this really depends on the bug. In any case, it is always worthwhile to try and turn a finding into a query.

Besides your own findings or if you don’t have too many findings yet, you can also do research on blog posts, post-mortems, etc. from other researchers. Nonetheless, from my experience these findings tend to be more saturated, so your own findings would be better.

Let’s take my Nouns DAO finding as an example. You can read more about it here: [https://mirror.xyz/verbsteam.eth/TP917T6vm6gXuVAxbQ34ZCn7dNiHabu3UW-ninwalVc](https://mirror.xyz/verbsteam.eth/TP917T6vm6gXuVAxbQ34ZCn7dNiHabu3UW-ninwalVc)

**Short Nouns summary:**

In Nouns implementations, it was possible to direct delegation to address(0) in a way that ended up “burning” votes or breaking accounting because `delegateBySig` can set a delegate to the zero address so `_moveDelegates` decrements the source’s votes without incrementing any destination, which lets an EOA delegate effectively burn votes and leaves delegated NFTs stuck in a non-transferable state.

This finding was the result of a query that I wrote based on the same finding I had in another protocol a year earlier. At the time, I did not have the ability to do a mass scan of all source code with Glider, so I was not able to find the same bug in other places. Once I had access to Glider, I was able to take this bug pattern and turn it into a query and find the same bug in multiple places. Nouns DAO was a still very active project and happily accepted the bug report, rewarding me with a bounty and a blog post.

Once we have a bug finding, we can start the query building.

***

#### 2) Query phase <a href="#id-2-query-phase" id="id-2-query-phase"></a>

Not all bug findings can always be turned into an efficient query. Like I said, sometimes the bug is very specific and unique to the protocol, so you’ll either need to abstract it further or only take a small amount of results.

A good bug that can be turned into a query well is a bug that can be generalized and limits the number of false positive results. Obviously, this is easier said than done, because generalized bug patterns in code are difficult to come by, and most are already known. As such, there will always be some kind of specificity that makes it difficult to generalize, but on the other hand, also gives it that uniqueness that will result in new findings.

Building a query is an iterative process; you start easy and small. It will return a lot of results, but that’s okay, because you’re going to add to it and shear away those false positives using the Glider syntax. If the bug you’re using as a base came from an on-chain contract, then that’s even better because you can use that contract as a metric. If that contract disappears from your results, it means you’re being too restrictive or the query is wrong.

Let’s look at an example. We want to build a query that can find the following code pattern:

Copy

```
function delegates(address account) external returns (address) {
    if (_delegates[account] == address(0)) {
        return account;
    }
    return _delegates[account];
}
```

This snippet of Solidity shows the overridden delegates function found in many governance tokens. It comes from the bug described in the blog post from Nouns above.

Copy

```
def query():
    res = (Functions()  # query all functions
        .with_signature("delegates(address)")  # with this signature
        .exec())
```

* What Glider is doing here : `Functions().with_signature("delegates(address)")` returns every function across the dataset that matches this exact signature. `.exec()` executes the query and gives you the list to iterate over.

We start simple and just build a query that returns us all the functions that match the signature.

Copy

```
def query():
    res = (Functions()  # query all functions
        .with_signature("delegates(address)")  # with this signature
        .exec())

    ret = {}
    for func in res:  # iterate the resulting functions
        sc = func.source_code()  # get the source code
        if 'address(0)' in sc:  # string/regex check for address(0)
            pass
    return list(ret.values())  # convert dict to list to return
```

* What Glider is doing in this pass: `.source_code()` gives the Solidity so a fast substring check prunes obvious non-matches. It’s quick and keeps the haystack smaller for the next step.

Then we need to iterate over the results with a loop. In there, we can unpack each individual function and do some more filtering, as not all functions with the signature are vulnerable per se. I perform a simple string check on the source code to see if ‘address(0)’ is in there. This is by no means perfect, as some false positives could fall through, but it does allow us to filter out true negatives, because having ‘address(0)’ is a hard requirement. Using a string comparison on the source code is also very fast.

Copy

```
def query():
    res = (Functions()  # query all functions
        .with_signature("delegates(address)")  # with this signature
        .exec())

    # The below pass filters delegates(address) function that do contain address(0)
    # (like in the example above), then checks any calls to _delegate in the contract
    # and check if they don't check for address(0), if so
    # it looks up the _delegate function and returns that for easier checking of results.
    ret = {}
    for func in res:  # iterate the resulting functions
        sc = func.source_code()  # get the source code
        if 'address(0)' in sc:  # string/regex check for address(0)
            for cf in (func
                        .get_contract()  # move up from function to contract
                        .functions()  # back to all functions in the contract
                        .with_callee_names(['_delegate'])  # query for functions that call _delegate
                        .exec()):
                cfsc = cf.source_code()  # check the source code of these functions
                pass
    return list(ret.values())  # convert dict to list to return
```

* What Glider is doing in the inner pass: We pivot from a single function to its parent contract via .get\_contract(), then grab sibling functions and filter by callee names (.with\_callee\_names(\['\_delegate'])).

After that, we perform an inner query again with ‘exec’. As you can see, it moves from the individual function back to the contract and to all of the functions in the contract to find all functions that call the internal function with the name ‘\_delegate’. This is because we want to find them and check if they handle the ‘address(0)’ case, because if one of them does, we want to filter it out.

Copy

```
def query():
    res = (Functions()  # query all functions
        .with_signature("delegates(address)")  # with this signature
        .exec())

    # The below pass filters delegates(address) function that do contain address(0)
    # (like in the example above), then checks any calls to _delegate in the contract
    # and check if they don't check for address(0), if so
    # it looks up the _delegate function and returns that for easier checking of results.
    ret = {}
    for func in res:  # iterate the resulting functions
        sc = func.source_code()  # get the source code
        if 'address(0)' in sc:  # string/regex check for address(0)
            for cf in (func
                        .get_contract()  # move up from function to contract
                        .functions()  # back to all functions in the contract
                        .with_callee_names(['_delegate'])  # query for functions that call _delegate
                        .exec()):
                cfsc = cf.source_code()  # check the source code of these functions
                if not 'address(0)' in cfsc:  # string/regex check for no address(0)
                    for gf in (cf
                                .get_contract()
                                .functions()  # iterate functions
                                .with_name('_delegate')  # and filter for name _delegate
                                .exec()):
                        ret[gf.get_contract().address] = gf  # add to results
    return list(ret.values())  # convert dict to list to return
```

* What the final filter accomplishes: We keep candidates where a call site into \_delegate does not visibly guard address(0) to make manual review faster.

You can see that here in the final query, where we do that string comparison for ‘address(0)’ being absent from the source code of the function that calls the ‘\_delegate’ function. If so, it will look up the actual ‘\_delegate’ function and add it to the results.

Once you have a query that correctly describes the bug pattern, we can go and try to filter the false positives further.

***

#### 3) Filtering phase <a href="#id-3-filtering-phase" id="id-3-filtering-phase"></a>

Glider is very powerful when it comes to finding patterns in code, but there are still some limitations when it comes to filtering on live values, such as balances or transactions.

So now that we have a large list of contracts that are potentially vulnerable to the bug, we need to do some further filtering of false positives. I like to use the Etherscan API and Dune for this. The Etherscan API can get you information about the contract’s balances (both ETH and ERC20), but this should not be a hard filter, but rather an order heuristic. With Dun,e you can easily get information about the last (internal) transaction that was made to the contract, giving you information on whether the contract is still used.

We can distinguish between elimination filters, i.e. do we want to cut-off any contracts that haven’t been active for more than 90 days, and order heuristics, i.e. order by last active date and asset balance. I don’t filter out contracts without balances, because it is very often the case that a protocol has a contract that is responsible for assets indirectly. So the contract could have no balance, but it could still have a bug that could lead to a full loss of principal assets.

You can download the results from Glider directly as JSON. Using a simple Python script, I usually do some data analysis and transformation on it, to feed it into a Dune query or the Etherscan API programmatically.

The result would be a smaller list of targets for which it is now time for manual analysis.

Using Dune we can order the list of contract addresses by activity, i.e. the last internal transaction timestamp. The following Dune query will do that for you:

Copy

```
WITH tx_counts AS (
    SELECT "to" AS address, COUNT(*) AS transaction_count, MAX(block_time) AS latest_transaction_date
    FROM ethereum.traces
    WHERE "to" IN ({{addresses}}) AND block_number > {{cutoff}}
    GROUP BY "to"
)
SELECT address, transaction_count, latest_transaction_date
FROM tx_counts
ORDER BY latest_transaction_date DESC
```

(Credits to [https://x.com/ustas\_eth](https://x.com/ustas_eth))

Here, the variable ‘addresses’ is the list of addresses that rolled out of Glider, and the variable ‘cutoff’ is the block timestamp in the past from where you want to cut off the searching; otherwise, the query will take too long. This will give you a list that is easier to work with for the manual phase.

Next up, you want to make it yourself easier by pulling the source code of the contracts all in one folder so that you don’t have to copy-paste the address in Etherscan and open the code. This way you can stay in your IDE and just browse/search through the code.

I like to use a Python script that interacts with the Etherscan API to download the source code. Here is part of the script that does that for me:

Copy

```
def do_req(url, headers={}):
    for _ in range(5):
        try:
            req = requests.get(url, headers=headers)
            return req
        except:
            sleep(0.5)
    exit("Failed to perform a request to %s" % url)

def pull_source(chain, addr):
    api = EXPLORER_APIS[chain]
    res = do_req(api['url'] + EXPLORER_SOURCE_PATH % (addr, api['key'])).json()['result'][0]
    sleep(0.2)
    if res['SourceCode'].startswith('{{'):
        asc = json.loads(res['SourceCode'][1:-1])['sources']
    else:
        try:
            asc = json.loads(res['SourceCode'])
        except:
            asc = {f"{res['ContractName']}.sol": {'content': res['SourceCode']}}
    return asc
```

***

#### 4) Manual phase <a href="#id-4-manual-phase" id="id-4-manual-phase"></a>

Your time is the most valuable resource, so manage it well.

After the filtering step, we now have a smaller list of potential targets for manual analysis. At this stage, the task is to look at the source code of each contract and determine whether it is vulnerable to the bug.

* Accessing source code
  * Check it directly on the chain’s explorer
  * Or automate with an Etherscan API script so you don’t need to leave your editor
* Challenges
  * It requires the same critical mindset as an auditor or bug hunter
  * The bug pattern might be present, but hidden as a variation
* Why it’s still easier with Glider
  * Heuristics and results from Glider have already led us to these contracts
  * You know where to focus, compared to a typical bug bounty search

***

#### 5) Exploitation phase <a href="#id-5-exploitation-phase" id="id-5-exploitation-phase"></a>

If we have any bug findings from the manual step, then we need to create proof-of-concepts for each one. Since they should all be similar, this can be done quickly and efficiently. This should not be skipped, as a well constructed bug report with a proof-of-concept as proof is worth a million shitty reports.

* How to build the PoC (recommended)
  * Use Forge from the Foundry suite.
  * Create a fork test that actually exploits the vulnerability.
  * Add comments that explain each action in the test.
  * Use logs to show the start, intermediate, and final states of the exploited protocol.

***

#### 6) Reporting phase <a href="#id-6-reporting-phase" id="id-6-reporting-phase"></a>

Now that we have a bug and a proof-of-concept, it is time to write a report and submit it to the protocol in question. To do this:

* Research whether the protocol has a bug bounty program
* If not, check whether the project has a disclosure page in their documentation with an e-mail address for reporting
* If neither option is available:
* Try to contact a tech lead through another communication channel (e.g., Discord)
* Alternatively, reach out to the auditing firm that reviewed the contracts, since they usually have direct communication with the team responsible for fixing bugs

***

#### 7) Conclusion <a href="#id-7-conclusion" id="id-7-conclusion"></a>

Glider transforms individual bug discoveries into scalable detection workflows. By encoding the “shape” of a vulnerability into a query, we can move beyond one-off findings and systematically uncover similar flaws across large codebases.

The key takeaway is that Glider enables security researchers to treat past incidents not just as isolated wins, but as blueprints for continuous detection. Combined with external data sources and careful manual analysis, this approach significantly increases both efficiency and impact in vulnerability hunting.

If you’re curious to see this query in action, you can explore it directly on the Glider Query Database. [Check it out here](https://r.xyz/glider-query-database/query/68db9acf00ba00239f2e3929)
