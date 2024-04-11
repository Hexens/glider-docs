---
description: >-
  Returns the parent contract of the function/modifier if exists, otherwise
  (global functions) returns NoneObject.
---

# Callable.get\_contract()

## Return type

→ [Contract](../contract/) | NoneObject

## Example

```python
from glider import *
def query():
  functions = Functions().with_modifiers_name_not(["onlyOwner"]).exec(100)

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
