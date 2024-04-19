---
description: Returns all the functions of a Contract.
---

# Contract.functions()

`functions() →` [`Functions`](../functions/)

The function returns all of the functions that the Contract has, including the inherited functions from its base classes.

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 1)
  
  names = []
  for contract in contracts:
    functions = contract.functions().exec()

    for function in functions:
      names.append(function.name())

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "_msgSender",
    "_msgData",
    "constructor",
    "owner",
    "renounceOwnership",
    "transferOwnership",
    "_setOwner"
  ]
}
```
