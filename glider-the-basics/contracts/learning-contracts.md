# Learning Contracts

## What are Contracts

A Solidity contract is a piece of executable code consisting of state variables, functions, modifiers, and more. Contracts form the backbone of Solidity applications, defining the logic and rules that run on the the EVM.

## Finding Contracts

Glider makes it easy to identify contracts using Glider’s Contracts class. Let’s see how this works by running the query below:

```python
from glider import *

def query():
    return Contracts().exec(10)
```

After running the query, you should see the first 10 contract results found by Glider displayed in the Output panel.

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-09 at 2.16.48 PM.png" alt="" width="375"><figcaption><p>Glider IDE contract output results</p></figcaption></figure>

## Foundational Contracts Query

Let's take a look at our foundational contracts query and break down the query code.

### **Query Goal**

We are interested in finding "Market" contracts that are eligible to receive ERC-721 tokens. To find these contracts, we will search for contracts that have the name "Market" in them and contain the "onERC721Received" function.&#x20;

The query is below:

```python
from glider import *

def query():
    contracts = (
        Contracts()
        .with_name_regex("Market")
        .exec(1000)
        .filter(lambda contract : "onERC721Received" in contract.functions().exec().name)
    )

    return contracts
```

Now let's start by breaking down each query into sections below.

### Step 1 - Finding Contracts

To find smart contracts, we first create an instance of the [Contracts class](https://glide.gitbook.io/main/glider-ide/api/contracts):

```python
Contracts()
```

#### **Filtering Contracts by Name Using Regex**

Next, we use the .with\_name\_regex() method provided by Glider. This method searches for contracts whose names match a given regular expression (regex).

Since we are looking for contracts that contain the term "Market", we pass "Market" as our regex pattern:

```python
Contracts().with_name_regex("Market")
```

This ensures that any contract with "Market" in its name - such as "NFTMarket", "TokenMarketplace", or "MarketExchange" will be included in the results.

### Step 2 - Filtering Contracts that Receive ERC-721 tokens

Now that we’ve queried for contracts with "Market" in their names, our next step is to ensure that our results only include contracts designed to receive ERC-721 tokens.

Contracts that expect to receive ERC-721 tokens must implement the onERC721Received function. If a contract does not define this function, it is not intending to receive ERC-721 tokens.

#### **Filtering with .filter()**

We add a .filter() method to our [method call chain](https://glide.gitbook.io/main/glider-ide/glider-the-basics/intro-to-python/basic-python#chaining-function-calls) to exclude contracts that lack the onERC721Received function. The filter uses a lambda function to apply this criterion:

```python
.filter(lambda contract: "onERC721Received" in contract.functions().exec().name)
```

#### **Breaking Down the .filter() Function**

Let’s take a closer look at how the .filter() function helps us refine our query results:

```python
.filter(lambda contract : "onERC721Received" in contract.functions().exec().name)
```

#### **Adding the Lambda Function**

The .filter() method takes a lambda function, which is applied to every contract in the query results.

```python
lambda contract : "onERC721Received" in contract.functions().exec().name
```

#### **Retrieving All Functions in Each Contract**

The lambda function first queries all functions in the contract:&#x20;

```python
contract.functions().exec()
```

Calling .functions() retrieves all defined functions in the contract and calling .exec() executes the query, returning a list of function objects.

#### **Checking for onERC721Received**

We then access the function names:&#x20;

```python
contract.functions().exec().name
```

This extracts the names of all functions defined in the contract.

Finally, calling "onERC721Received"`in` tells Glider to check if "onERC721Received" is  inside the list of function names.&#x20;

```python
"onERC721Received" in contract.functions().exec().name
```

{% hint style="info" %}
**Tip**: When we have a list of strings and want to check if a specific string exists in that list, we use the in keyword:

```python
"term to look for" in list
```
{% endhint %}

If the function name exists in the list, the expression returns True. If the function does not exist, the expression returns False.

#### **Filtering Out Results**

Since .filter() only keeps results where the lambda function evaluates to True. This ensures that:

* Contracts defining onERC721Received remain in the results.
* Contracts without onERC721Received are filtered out.

This guarantees that our query only includes contracts capable of receiving ERC-721 tokens.

### Step 3 - Returning Contracts

Once we’ve completed our query and filtered out unwanted results, we assign the final results to a variable named contracts and return it in the query() function:

```python
return contracts
```

This ensures our results will be displayed in the Glider IDE Output panel.

## Query Results

### **Running the Query**

Now that we’ve covered the query, let’s run it in Glider IDE.

Paste the following query into the Glider IDE, click “Run”, and wait for the results:

```python
from glider import *

def query():
    contracts = (
        Contracts()
        .with_name_regex("Market")
        .exec(1000)
        .filter(lambda contract : "onERC721Received" in contract.functions().exec().name)
    )

    return contracts
```

### **Interpreting the Results**

Once the query completes, Glider returns a list of contracts and their addresses. Each contract in the results:

* Contains "Market" in its name, as specified in our query.
* Defines the onERC721Received function, confirming it is designed to receive ERC-721 tokens.

This ensures we have successfully filtered contracts that both match the "Market" naming criteria and are capable of handling ERC-721 token transfers.
