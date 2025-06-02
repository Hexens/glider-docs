# Understanding Components

## What are Components

Every instruction is made up of components. These components represent the anatomy of instructions. Every instruction can contain 1 or more components. Components can represent everything from variables, function calls, expressions, and more.&#x20;

When we want to inspect an instruction, we will almost always query for the components of an instruction. For example, take the following Solidity instruction:

```solidity
changeOwnership(newOwner);
```

If we retrieve the instruction's components, Glider will return a single component:

* `changeOwnership(newOwner)`: The function call.

This component can be further queried to identify the call arguments,  the call name, where the call arguments come from, and more.&#x20;

With components, we can make our query granular and glean additional information from Solidity, both critical aspects to writing excellent queries.

## How to Query For Components

How do you query for components? Components can be queried by calling `get_components()` on an Instruction. For example, consider the following query:

```python
def query():
    instructions = Instructions().new_variable_instructions().exec(1, 10)
    
    instruction = instructions[0]
    
    return instructions
```

This query returns us the following Solidity instruction:

```solidity
address feeTo = IPancakeFactory(factory).feeTo();
```

So how do we query for the components. With the instruction variable, we can call `instruction.get_components()` . Let's also print out the components by wrapping it in a print statement. Our query now looks like:

```python
def query():
    instructions = Instructions().new_variable_instructions().exec(1, 10)
    
    instruction = instructions[0]
    print(instruction.get_components())
    
    return instructions
```

If we run this query, we will see that the following printed out in the Glider IDE debug panel \[EDIT: make sure that is the terminology we use throughout this entire course]:

```python
[<api.value.call.Call object at 0x700bda286110>]
```

We can see that Glider has returned to us a single component in an array. Let's look at another example of an instruction and what happens when we query for it's components. Below you can see our Instruction:

```solidity
uint liquidity = numerator / denominator;
```

If we get the components of the instruction, we will be returned the following components:

```
[
    <api.point.var_value.VarValue object at 0x7267f10fb460>, 
    <api.value.operator.Operator object at 0x7267f10fbdc0>, 
    <api.point.var_value.VarValue object at 0x7267f10fb2e0>
]
```

Although we don't know yet how to work with these components and what each component means, we can understand that every instruction has components.

## What About Querying For Assigned Variables?

In Solidity, it's common to come across an instruction that assigns a variable. For example:

```solidity
address userBalance = balances[msg.sender];
```

Here `userBalance` is assigned. If we call `get_components()` , Glider will _not_ return a component that represents the assigned variable. If you want to query for the assigned variables, check out our next section on dests \[INSERT LINK TO DESTS HERE].

## Component Types

Although we will discuss component types in a future section \[INSERT LINK TO VALUES SECTION], we will briefly mention that there are many component types that can be returned to us. Below is a short list of the most common type of components you will come across:

* Calls: Calls are function calls
* VarValues: Represent variables
* ValueExpressions: This represents the smallest amount of code that evaluates to a value.

We will discuss more on component types in the Values section \[INSERT LINK TO VALUES SECTION].



