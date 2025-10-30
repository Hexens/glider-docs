---
icon: '3'
cover: ../.gitbook/assets/Frame 1.png
coverY: 0
---

# How to Write a Great Glider Query - Finding Arbitrary Calls

Article by [@_mr\_thank\_you_](https://x.com/_mr_thank_you_)

## Intro <a href="#intro" id="intro"></a>

As a security researcher interested in security tools, one of the most powerful web3 tools I've found in this space is Glider. It is hands down one of the best tools on the market for finding Solidity code patterns in deployed contracts. With Glider, I can write a Glider query that looks for the same vulnerability in other deployed on-chain contracts across multiple chains.

I have used this approach many times and it has led me to write many queries, looking for either common, uncommon, or exceptionally rare bugs.

Some things I've learned from Glider while doing this research is that:

* Common bugs will result in a lot of results. This is both good and bad. Good in that you likely have vulnerabilities. Bad in that you have to review a lot of results, which requires more time and effort.
* Uncommon and rare bugs result in less results.
* Uncommon and rare bugs are typically harder to write in Glider due to additional complexity due to the bug.

With these restraints in mind, I believe it's paramount to think carefully about what type of vulnerability you want to find with Glider. To demonstrate why this is the case, this article will walk through a real-world example of finding a common exploit and converting it to a Glider query.

### Finding Great Queries <a href="#finding-great-queries" id="finding-great-queries"></a>

As a security researcher looking for bugs live on-chain, I'm interested in finding bugs not found during the audit process. These bugs typically take more effort to find or can be missed if the auditor is too tired. In my experience, the type of Glider query I want to find is:

* Something that nets me only a few but valuable results from Glider.
* A query that isn't difficult to write.
* A query that is based on the real-world. If the bug was found in the wild or in audits multiple times, the more likely I'll find the bug elsewhere too.

It's sometimes difficult to encapsulate how to know whether or not a bug fits these requirements. And sometimes the best decision is to write the query and see what you come up with. All that said, I'll explain a bug I wrote a query for and why it was a great candidate for Glider bug bounty hunting.

### Real World Example - Arbitrary calls <a href="#real-world-example-arbitrary-calls" id="real-world-example-arbitrary-calls"></a>

Each week, I review live exploits and their post-mortems. If I start finding multiple reports that cover the same vulnerability, I begin to internalize the commonalities of the bug. One bug I discovered happened over several projects. Below you can find brief descriptions of the bugs I found:

#### Seneca Hack 2024 <a href="#seneca-hack-2024" id="seneca-hack-2024"></a>

Seneca experienced a vulnerability where users can provide arbitrary bytes that were decoded via abi.decode. These decoded values are used to make an arbitrary call. In this case, the hacker made an arbitrary call to transfer tokens that were approved to be spent by Seneca's contract to the malicious user.

Source: [https://www.cyfrin.io/blog/seneca-attack-hack-analysis-proof-of-concept](https://www.cyfrin.io/blog/seneca-attack-hack-analysis-proof-of-concept)

#### Moonhacker 2024 Hack <a href="#moonhacker-2024-hack" id="moonhacker-2024-hack"></a>

Moonhacker was susceptible to an issue where an arbitrary user was able to pass in encoded bytes that included an arbitrary token address. This protocol approved the arbitrary token address to receive tokens via ERC20.approve() and the malicious user was then able to withdraw funds from the protocol.

Source: [https://blog.solidityscan.com/moonhacker-vault-hack-analysis-ab122cb226f6](https://blog.solidityscan.com/moonhacker-vault-hack-analysis-ab122cb226f6)

#### Arcadia Hack 2025 <a href="#arcadia-hack-2025" id="arcadia-hack-2025"></a>

The Arcadia hack led to a $3.6 million dollar exploit. This exploit occurred because Arcadia decoded bytes via abi.decode and then passed the decoded data to a low-level call. Notably, the decoded bytes defined what contract was to be called and and the function signature.

Source: [https://blog.solidityscan.com/arcadia-finance-hack-analysis-a03a722e554d](https://blog.solidityscan.com/arcadia-finance-hack-analysis-a03a722e554d)

### Compiling Findings <a href="#compiling-findings" id="compiling-findings"></a>

Based on these findings, I was able to identify the following commonalities between each of these exploits:

1. User input is passed into abi.decode

This was an aha moment for me. While reviewing uses of abi.decode in contracts, I kept finding a recurring pattern. Decoded bytes are almost always sourced from users. This makes sense since a contract rarely ever stores arbitrary bytes and then later decodes it. Instead, contracts receive bytes in the function arguments (often user-controlled) and decode the bytes during code execution.

2. Decoded bytes are used in association with making an arbitrary low-level call

Decoded bytes are often used to execute complex operations. Some of these cases include router contracts swapping tokens, bridges executing arbitrary calls, or a contract implementing multiple calls. Regardless of the purpose, low-level calls almost always follow abi decoding.

### Outline of Query <a href="#outline-of-query" id="outline-of-query"></a>

Based on these commonalities, how do I convert this into a Glider query?

I see two things the query needs to do:

1. Identify Solidity code that calls abi.decode
2. Decoded bytes from abi.decode are used in a low-level call.

There are other things I can check that add complexity to this query. For example, I can check if the encoded bytes come from a function argument or if the function called is public/external. That said, I'll ignore these for now as I don't know how often I'll find these in my results and for the purpose of this article I want to keep things simple.

### Writing the Query <a href="#writing-the-query" id="writing-the-query"></a>

Based on these two needs, we can break up the query into the following sections:

#### Step 1 - Find Instructions containing low-level calls <a href="#step-1-find-instructions-containing-low-level-calls" id="step-1-find-instructions-containing-low-level-calls"></a>

This is easy as all we have to do is:

```
# Find low-level external calls 
low_level_calls = Instructions().low_level_external_calls().exec()  
```

This code will return Instructions (aka lines of code) that contain low-level external calls.

#### Step 2 - Check if abi.decode is called in an Instruction <a href="#step-2-check-if-abidecode-is-called-in-an-instruction" id="step-2-check-if-abidecode-is-called-in-an-instruction"></a>

In Glider, when we have an Instruction and want to see if abi.decode() is called in the Instruction, we can call `callee_names()` against the Instruction. This function will return every call name made in the Instruction. For example, the following Glider query code will return an array containing function names called in the Instruction including "abi.decode":

```
# Returns ["abi.decode"] when the instruction looks like this:
# 
# (x, addr, arr) = abi.decode(data, (uint256, address, uint256[]));
# 

# Returns ["abi.decode"] if abi.decode is called in the instruction.
instruction.callee_names() 
```

#### Step 3 - Find the low-level call from the Instruction <a href="#step-3-find-the-low-level-call-from-the-instruction" id="step-3-find-the-low-level-call-from-the-instruction"></a>

> Note: This step is a bit longer than others as it covers the most critical aspect of this query, connecting the dots between abi.decode and low-level external calls.

When we find an Instruction that calls abi.decode, we need to retrieve the Call object. The Call object is a reference to the Solidity function being called. In this case, we need to look for a Call object that is the Solidity low-level call.

> Note: Instructions are made up of components. The component we want to look for is a Call. Once we have the Call object, we can query further and identify specific info about the Call.

To find a Call in an Instruction, I created a handy snippet of code that finds all components of an Instruction:

```
def get_components_recursive(component):
    components = []

    try:
        # Get components of an IndexAccess
        if "IndexAccess" in str(component): 
            components.append(component.get_sequence()) 
            components.append(component.get_index())

        # If we are dealing with a call, we get the call arguments as components
        if isinstance(component, Call):
            components = component.get_args()
            call_qualifier = component.get_call_qualifier()

            # Get components of an IndexAccess
            if "IndexAccess" in str(call_qualifier): 
                components.append(call_qualifier)
                components.append(call_qualifier.get_sequence()) 
                components.append(call_qualifier.get_index())
        else:
            # Get components within components
            components = component.get_components()
    except Exception:
        # This handles cases where the component can't be broken down further
        None

    results = []

    for comp in components:
        results.append(comp)
        for sub_comp in get_components_recursive(comp):
            results.append(sub_comp)
    
    return results
```

> Note: You can use this in your own query if you want too!

Now we can get the components of the Instruction by calling:

```
low_level_calls = Instructions().low_level_external_calls().exec(1) 
instruction = low_level_calls[0] # Get the first Instruction we find

# Here we pass the instruction variable into get_components_recursive()
components = get_components_recursive(instruction) # get_components_recursive returns an array of components
```

Now that we have an array of components, how do we find the low-level Call from the components?

We can achieve this by doing the following:

```
for component in get_components_recursive(instruction):
    if isinstance(component, Call) and component.name == "call":
        # Do stuff with the component variable as it's a low-level call
```

In the code above, we walk through each component, check if it's a Call object, and check if the function called is named "call" which represents a Solidity low-level call.

#### Step 4 - Find decoded bytes flowing to low-level calls <a href="#step-4-find-decoded-bytes-flowing-to-low-level-calls" id="step-4-find-decoded-bytes-flowing-to-low-level-calls"></a>

What we need to do now is determine if the decoded bytes are used in a low-level call. Let's consider this Solidity code example:

```
// We presume the blob variable comes from the user
(address target, bytes memory callData) = abi.decode(blob, (address, bytes));

// decoded bytes used directly in a low-level call
(bool ok, bytes memory ret) = target.call(callData);
```

Looking at this example, we see that the blob variable is decoded into two variables, target and callData. In Glider, if we want to see if the decoded bytes flow to a low-level call, we first get the target and callData variable inside of the low-level call:

```
# Code omitted above for brevity

components = get_components_recursive(instruction)

for component in get_components_recursive(instruction):
    if isinstance(component, Call) and component.name == "call":
        # get_call_qualifier() gets the `target` variable of the low-level call, aka the contract that is called
        target_variable = component.get_call_qualifier()
        
        # get_arg(0) tells Glider to find the first argument in the Call object, which is going to be the calldata argument.
        calldata_variable = component.get_arg(0)
```

> Note: Some Glider functions like get\_call\_qualifier() and get\_arg() are not explained in full detail here. For more info on these functions and all available Glider API methods check out the Glider API documentation [here](https://glide.gitbook.io/main/glider-ide/api).

With this Glider query, I can now identify low-level calls and each low-level call's target contract and calldata.

#### Step 5 - Find out where the variables came from <a href="#step-5-find-out-where-the-variables-came-from" id="step-5-find-out-where-the-variables-came-from"></a>

Here’s where Glider really shines.

Once I have the target contract and the calldata from the low-level call, I can use a powerful Glider API function called `backward_df_recursive()` to see where the variables originated. Glider refers to this as data flow ("df").

This Glider API function is powerful because it can scan across multiple functions. That means if the variable came from another function, it can find that function too and trace the data flow.

`backward_df_recursive()` will return an array of instances where the variable in question is used. These instances inside the array are called Points.

Let's go ahead and call `backward_df_recursive()` against the calldata\_variable and target\_variable Glider Python variables:

```
# Code omitted above for brevity

target_variable.backward_df_recursive() # This returns an array of Points where the variable is used. 
calldata_variable.backward_df_recursive() # This returns an array of Points where the variable is used. 
```

Now let's loop through each of the Points returned by `backward_df_recursive()`:

```
for point in target_variable.backward_df_recursive():
    print(point) # Prints out the point
```

With each Point, we can see if the Point is an Instruction (sometimes Points are not instructions) and abi.decode is called. We can do this by looking back at Step 2 and call callee\_names() against the Instruction:

```
for point in target_variable.backward_df_recursive():
    if isinstance(point, Instruction) and "abi.decode" in point.callee_names():
        print("target variable is connected to a decoding")
```

If all goes well, we will get a printout in the Output panel in Glider IDE that the target variable is sourced from abi.decode.

#### Step 6 - Finalize the query <a href="#step-6-finalize-the-query" id="step-6-finalize-the-query"></a>

Now that we have built all the components to the query, let's go ahead and put everything together:

```
def query():
    # Find low-level external calls 
    low_level_calls = Instructions().low_level_external_calls().exec(100)  

    # Iterate through all low level calls
    for instruction in low_level_calls: 
        # Get all components making up the instruction
        components = get_components_recursive(instruction)

        # Iterate through all components
        for component in components:
            # Let's check that the component is a Call object and it's the low-level external call we are looking for.
            if isinstance(component, Call) and component.name == "call":
                # In rare cases a call may not have any arguments, so we skip it for now as a sanity check.
                if len(component.get_args()) == 0:
                    continue
                     
                # get_call_qualifier() gets the `target` variable of the low-level call, aka the contract that is called
                target_variable = component.get_call_qualifier()

                # Get the first argument which represents the calldata
                calldata_variable = component.get_arg(0)

                # Iterate through all Points where the target contract variable lies
                for point in target_variable.backward_df_recursive():
                    # If the point is an instruction and it calls abi.decode, we have a hit.
                    # We do the isinstance check against the point variable because backward_df_recursive() can return non-instructions.
                    if isinstance(point, Instruction) and "abi.decode" in point.callee_names():
                        print("found target variable coming from abi.decode")

                for point in calldata_variable.backward_df_recursive():
                    # If the point is an instruction and it calls abi.decode, we have a hit.
                    # We do the isinstance check against the point variable because backward_df_recursive() can return non-instructions.
                    if isinstance(point, Instruction) and "abi.decode" in point.callee_names():
                        print("found calldata variable coming from abi.decode")


    return Instructions().exec(1)

def get_components_recursive(component):
    components = []

    try:
        # Get components of an IndexAccess
        if "IndexAccess" in str(component): 
            components.append(component.get_sequence()) 
            components.append(component.get_index())

        # If we are dealing with a call, we get the call arguments as components
        if isinstance(component, Call):
            components = component.get_args()
            call_qualifier = component.get_call_qualifier()

            # Get components of an IndexAccess
            if "IndexAccess" in str(call_qualifier): 
                components.append(call_qualifier)
                components.append(call_qualifier.get_sequence()) 
                components.append(call_qualifier.get_index())
        else:
            # Get components within components
            components = component.get_components()
    except Exception:
        # This handles cases where the component can't be broken down further
        None

    results = []

    for comp in components:
        results.append(comp)
        for sub_comp in get_components_recursive(comp):
            results.append(sub_comp)
    
    return results
```

### Trying The Queries Yourself <a href="#trying-the-queries-yourself" id="trying-the-queries-yourself"></a>

At this point, the query is complete and ready to detect potential vulnerabilities!

You can run it yourself directly in the Glider IDE [here](https://glide.r.xyz/query/c1c783e4-ac34-45f1-95e5-b516974b3fbc)!

Furthermore, if you want to improve the query and level-up your own Glider skills and research, you can apply the following changes:

* Filter out false positives by excluding functions via their names, since many duplicates appear when forked contracts reuse the same code.
* Filter out functions that use OpenZeppelin’s nonReentrant modifier.
* Add a check to confirm that the target contract is validated in a require check.

### Conclusion <a href="#conclusion" id="conclusion"></a>

Through reviewing various bug report submissions, I was able to identify a commonality among various exploits. These commonalities were then translated into a Glider query that allowed me to identify verified deployed contracts that may be impacted by the same bug in numerous exploits.

One of the most daunting and time-consuming parts of bug hunting is finding the vulnerable contracts. As we can see, with Glider I am able to identify live potentially vulnerable contracts with just a single Glider query.

If you're interested in trying out Glider IDE and learning more about how to write Glider queries, check out the links below:

* [Glider IDE](https://glide.r.xyz/)
* [Glider API documentation](https://glide.gitbook.io/main/glider-ide/api)
