---
description: High-level introduction to the query framework
---

# Glider introduction

Glider is a code query engine designed to run variant and data analysis on smart contracts by providing a framework that gives anyone the ability to query contract code as one would do with data.

The researcher writes a query (called a glide) describing a scenario of code he wants to match and runs it against any type of codebase; specifically, now, it can be run against whole blockchains that are integrated into the system.

Example of a glide:

<pre class="language-python"><code class="lang-python">from glider import *
def query():
  # <a data-footnote-ref href="#user-content-fn-1">iterate</a> over all of the instructions in the blockchain
  # and find the ones that call selfdestruct()
  instructions = Instructions().with_callee_function_name('selfdestruct').exec(100)
  return instructions
</code></pre>

An example output (from Kovan testnet):

```json
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

This is a playbook example; in fact, the Glider gives the ability to describe much more complex scenarios (such as traversing CFG/DFG graphs) in smart contract code and to find the ones that match it.

The core concepts of the engine are scalability, distribution and reusability.&#x20;

## Scalability

Glider gives the possibility to do variant analysis and security research on the scale of all open-source (verified) smart contracts across integrated EVM blockchains at breakneck speed. With its taint analysis and other advanced features, Glider represents a paradigm shift in code analysis.

## Distributable

Giving a unified and easy-to-use interface to code, Glider's main mission is to be a framework that can be distributed to and used by the community for greater impact on the whole industry.

One of the reasons why Glider does not introduce a new language for queries and rather uses Python syntax is to smoothen the learning curve, make it more accessible for everyone and also give more flexibility to the framework to integrate external tools.

## Reusability

The above mentioned concepts make gliders reusable, and while the ability to describe scenarios is distributed, the reported gliders can be reused by everyone and even be improved by other users.

[^1]: 
