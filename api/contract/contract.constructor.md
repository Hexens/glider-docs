# Contract.constructor()

## Description

It returns the constructor function of a Contract, if exists.

## Return type

([NoneObject](../noneobject/) | [Function](../function/))

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(10)
  
  constructors = []
  for contract in contracts:
    constructor = contract.constructor()

    if not isinstance(constructor, NoneObject):
      constructors.append(constructor)

  return constructors
```

## Example output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "constructor() {\n        _setOwner(_msgSender());\n    }"
}
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "ERC721",
  "sol_function": "constructor(string memory name_,string memory symbol_) {\n        _name = name_;\n        _symbol = symbol_;\n    }"
}
```
