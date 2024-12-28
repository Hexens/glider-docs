---
description: >-
  Returns the parent contract of the function/modifier if exists, otherwise
  (global functions) returns NoneObject.
---

# Callable.get\_contract()

`get_contract() →` [`Contract`](../contract/) `| NoneObject`

The function may return NoneObject in cases where it does not belong to any contract and is a global function, as Solidity supports that type of functions.

## Example

```python
from glider import *
def query():
  functions = Functions().without_modifier_names(["onlyOwner"]).exec(100)

  contracts = []
  for function in functions:
    # For each function without an "onlyOwner" modifier, return the contract
    contracts.append(function.get_contract())

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
