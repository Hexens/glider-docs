# What Are Values

## Understanding Values

As discussed in our Understanding Components section \[INSERT LINK], components represent the different parts of an Instruction. When we are dealing with a component, we are actually dealing with a Value. There are many types of Values, each representing a different type of Solidity code.&#x20;

For example, below are a list of different Solidity code that are Values and what their component types are:&#x20;

* `_msgSender()` - represents a Call
* `1e18` - represents a Literal
* `map[msg.sender][_salt]` - represents an IndexAccess
* `tokenIds.length` - represents a ValueExpression
* `userBalance` - represents a VarValue

As we can see, Glider identifies sections of Solidity code and converts them into Values. Once we have access to these Values we can do all sorts of things. We will discuss more about how to access and work with these Values below. But first, let's discuss why it's important to understand Values.



## Why Are Values Important

Values represent components of Solidity code. Often times when we are querying for Solidity vulnerabilities or code patterns, we are looking for clues or insights that can point us to the code we are interested in. By querying Values, we can have Glider identify specific types of code, not only granulaizing our query but also providing us excellent return results.

For example, by querying values, we can do the following:

* Identify a function call and check what arguments are passed to it
* Check if a variable is validated via an if statement or require/assert
* Learn where a function argument&#x20;

These features allows us to query all sorts of bugs such as:

* Missing ecrecover checks
* Missing user-input validations
* Lack of slippage protection based on oracle prices

By understanding what Values are and how they can be used in a query, Glider users will be able to successfully write sophisticated and powerful Glider queries that identify everything from 0-day vulnerabilities to common code patterns.



