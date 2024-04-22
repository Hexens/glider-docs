---
description: High-level introduction to the query framework
---

# Glider introduction

Glider is a code query engine designed to run variant and data analysis on smart contracts by providing a framework that gives anyone the ability to query contract code as one would do with data.

The researcher writes a query (called a glide) describing a scenario of code they want to match and runs it against any type of codebase; specifically, now, it can be run against whole blockchains that are integrated into the system.

Example of a glide:

```python
from glider import *
def query():
  # iterate over all of the instructions in the blockchain
  # and find the ones that call selfdestruct()
  instructions = Instructions().with_callee_function_name('selfdestruct').exec(100)
  return instructions
```

An example output (from Kovan testnet):

```solidity
{
"contract":"0xcFd05BebB84787EE2EfB2eA633981E44d754485d"
"contract_name":"AdminAuth"
"sol_function":
function kill() public onlyAdmin {
        selfdestruct(payable(msg.sender));
    }
"sol_instruction":
selfdestruct(payable(msg.sender))
}
```

This is a playbook example; in fact Glider gives the ability to describe much more complex scenarios (such as traversing CFG/DFG graphs) in smart contract code and to find the ones that match it.

The core concepts of the engine are scalability, distribution and reusability.&#x20;

## Scalable

Glider gives the possibility to do variant analysis and security research on the scale of all open-source (verified) smart contracts across integrated EVM blockchains at breakneck speed. With its taint analysis and other advanced features, Glider represents a paradigm shift in code analysis.

## Distributable

Giving a unified and easy-to-use interface to code, Glider's main mission is to be a framework that can be distributed to and used by the community for greater impact on the whole industry.

One of the reasons why Glider does not introduce a new language for queries and rather uses Python syntax is to smoothen the learning curve, make it more accessible for everyone and also give more flexibility to the framework to integrate external tools.

## Reusable

The above mentioned concepts make glides reusable, and while the ability to describe scenarios is distributed, the reported glides can be reused by everyone and even be improved by other users and the community.
