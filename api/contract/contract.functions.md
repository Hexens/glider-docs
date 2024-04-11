# Contract.functions()

## Description

Returns all the functions of a Contract.

## Return type

[Functions](../functions/)

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
