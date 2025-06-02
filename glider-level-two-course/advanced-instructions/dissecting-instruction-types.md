# Dissecting Instruction Types

When working on Glider queries, understanding the anatomy of an Instruction becomes critical when wanting to identify security vulnerabilities. This section will first cover common types of instructions. Once we understand type of instructions, we will then be able to break down the anatomy of instructions.



## Recap of Instructions



Instructions typically represent single lines of Solidity code. Through Glider, every line of code represents an instruction. In order to query lines of code. Glider assigns a type to each instructions.

Instructions can be broken up into a variety of types like function calls, return statements, if statements, try/catch statements, new variables, etc.

## Types of Instructions

There are many types of instructions. When writing a query, it is often helpful to understand what type of instruction you want to query. Below are the most common instructions you come across. Here we will provide not only the Instruction type but also provide a Solidity example and how to query for this in Glider.

### Finding Any Type of Instruction

In order to query for Instructions, we can run the following code:

```python
def query():
    return Instructions().exec(10)
```

Running this query will return the first 10 instructions Glider finds.&#x20;

Below we will see types of instructions we may experience with in Glider. For each instruction, we will not only explain what the instruction type is but we will also explain how you can update the Glider query above to query just for that given instruction.

### Expression Instruction

Expression instructions are one of the most common type of instructions you will find in Glider results. Expression instructions typically execute code or perform actions. This includes things like function calls, logic checks, variable assignments, and more.

Expression instructions can look like any of the following Solidity statements:

```solidity
require(isContract(_newFeeToken),"New address is not a token")

_totalSupply += amount;

emit OwnershipTransferred(_owner,newOwner);
```

In order to query for expression instructions, we can use the `expression_instructions()` function. Looking back at the Glider query above `Instructions().exec(10)` , we can modify this query to look for just expression instructions by appending `expression_instructions()` after we call `Instructions()` :

```python
def query():
    return (
        Instructions()
        # Adding expression_instructions() will tell Glider to query for expression 
        # instructions. 
        .expression_instructions()
        .exec(3, 10)
    )
```

If we run this query in the Glider IDE, Glider will return the following results:

<figure><img src="../../.gitbook/assets/Screenshot 2025-05-13 at 12.59.36 PM.png" alt=""><figcaption><p>Expression Instruction Glider Query Results</p></figcaption></figure>

By querying for expression instructions, we can identify various expressions that can be used to identify various code snippets.

### Call Instructions

Call instructions represent instructions that contain Solidity code calling another function. Since calling functions can occur in many types of Solidity, we can find calls anywhere from if instructions to return instructions as seen in the Solidity examples below:

```solidity
// A call made in if statement conditional
if (canBid(msg.sender) {

// A call made in the return statement
return totalBalance();

// A call is made that validates the msg.sender
enoughAmountProvided(msg.value);
```

When we query for call instructions, we will find that Glider returns to us all types of instructions. All Glider cares about is whether the instruction contains a call. If it does return a call, then the instruction will be returned.

To query for call instructions, we can run the following Glider query where we call `calls()`:

```python
def query():
    return (
        Instructions()
        .calls()
        .exec(2,5)
    );
```

If we run this in the Glider IDE, Glider IDE will return the following output:

<figure><img src="../../.gitbook/assets/Screenshot 2025-05-13 at 2.25.19 PM.png" alt=""><figcaption><p>Call Instruction Glider Query Results</p></figcaption></figure>

In the screenshot above, we can see that Glider returns to us two instructions, one is a require statement and another is a return statement. Both instructions contain calls to other functions.

Querying for call instructions is a great way to identify all calls made in a function. For most Solidity vulnerabilities, calls are a critical aspect to how the exploit occurred. By identifying call instructions, a Glider query can narrow down results and help identify vulnerabilities.&#x20;

### New Variable Instruction

In Solidity, one of the most common scenarios is defining new variables. When Solidity defines and assigns a new variable, the line of code assigning the new variable is a New Variable Instruction.

For example, the following Solidity code below represents a New Variable instruction

```solidity
uint256 userBalance = balances[msg.sender];
```

And another example:

```solidity
(address bidWinner, uint256 bidAmount) = bidInfo();
```

In order to identify new variable instructions, we can call `new_variable_instruction()`.  We can see this in the following example below:

```python
 def query():
    return  (
        Instructions()
        .new_variable_instructions()
        .exec(2)
    )
```

If we run this Glider query in the IDE, we will get back the following results:

<figure><img src="../../.gitbook/assets/Screenshot 2025-05-12 at 7.44.43 PM.png" alt=""><figcaption><p>New Variable Instruction Glider Query Results</p></figcaption></figure>

In the results, we can see Glider identified and highlighted two instructions where a new variable is created:

```
uint256 c = a + b;
```

and..

```
uint256 c = a - b;
```

By filtering new variable instructions, we can identify cases where Solidity takes a value, assign that value to a variable, and that variable is used later on.  More on that in the VarValue section \[INSERT THE LINK TO VAR VALUE SECTION].

#### If Instruction

If instructions represent if statements in Solidity. In Solidity, an if statement in Solidity looks like:

```
if (msg.sender == owner) {
    // Omitted for brevity
}
```

To identify if instructions, you can use the `if_instructions()` Glider function to query for if instructions:

```python
def query():
    return (
        Instructions()
        .if_instructions()
        .exec(1, 4)
    )
```

If you run this query in Glider IDE, you'll see the following result:

<figure><img src="../../.gitbook/assets/Screenshot 2025-05-12 at 10.15.58 PM.png" alt=""><figcaption><p>If Instruction Glider Query Results</p></figcaption></figure>

Here Glider identifies the following if statement:

```python
if (_initializationCalldata.length > 0) {
    _initialize(_implementation,_initializationCalldata);
}
```

With if instructions, we can get additional information from the if statement such as the condition and the instructions inside of the if statement bodies.

Finally, if instructions also can identify if/else statements.&#x20;

### Return Instruction

When a Solidity function returns a value, Solidity uses the return keyword:

```python
return owner;
```

Glider can identify the return statements in a Solidity function. In Glider, these are called return instructions.&#x20;

To query for return instructions, you can use the `return_instructions()` :&#x20;

```python
def query():
    return (
        Instructions()
        .return_instructions()
        .exec(10)
    )
```

In Glider IDE, we will see the following results returned:

<figure><img src="../../.gitbook/assets/Screenshot 2025-05-13 at 10.17.32 AM.png" alt=""><figcaption><p>Return Instruction Glider Query Results</p></figcaption></figure>

`return_instructions()` also identifies cases where a Solidity function contains multiple return statements! For example, in the Solidity function below, Glider will identify every return statement:

```solidity
function userDescription() public pure returns (string memory) {
    if (userBalances[msg.sender] > 1000e18) {
        // Glider identifies statement below as a Return Instruction
        return "Whale";
    } else {
        // Glider identifies statement below as a Return Instruction
        return "Trader";
    }
}
```

## Wrapping Up

There are many more types of instructions users can work with. Although we've gone over only a few of the instructions, other instruction types include:

* Try Instructions - Identifies cases where a try statement is called.
* ASM block instructions- Identifies assembly instructions inside of an assembly block.
* New contract instructions - Identifies where a new contract is created.

By understanding instruction types, we can create more efficient queries that identify specific lines of code we are looking for.&#x20;

In the next section, we will cover how to retrieve newly created variables in an instruction.
