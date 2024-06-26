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

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "IERC721"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "IERC721Metadata"
  },
  ...
]
```
