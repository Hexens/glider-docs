---
description: >-
  Returns a Modifiers object representing the modifiers through which the
  functions from current Functions object could be called.
---

# Functions.extended\_caller\_modifiers()

`extended_caller_modifiers() →` [`Modifiers`](../callables/modifiers/)

The function will retrieve _**extended**_**/**_**inter-procedural**_ modifiers, meaning it works recursively. It returns the Modifiers object representing all the modifiers that ultimately call the function in question.

## Query Example

```python
from glider import *

def query():
  funcs = Functions().with_name("onlyOwner").extended_caller_modifiers().exec(2)
  
  return funcs
```

## Output Example

```solidity
{
  "content": [
    {
      "contract": "0x80469265317ff8f00c3ce16576949986cebbc543",
      "contract_name": "OwnedUpgradable",
      "sol_modifier": solidity
        modifier onlyOwnerIfSet() {
            address theOwner = OwnableStorage.getOwner();
    
            // if owner is set then check if msg.sender is the owner
            if (theOwner != address(0)) {
                OwnableStorage.onlyOwner();
            }
    
            _;
        }
      "sol_modifier_souce_line": 88
    },
    {
      "contract": "0x80469265317ff8f00c3ce16576949986cebbc543",
      "contract_name": "OwnedUpgradable",
      "sol_modifier": solidity
        modifier onlyOwner() {
            OwnableStorage.onlyOwner();
    
            _;
        }
      "sol_modifier_souce_line": 79
    }
  ]
}
```
