# Contract.modifiers()

## Description

Returns all the modifiers of a Contract.

## Return type

[Modifiers](../modifiers/)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(10, 10)
  
  result = []
  for contract in contracts:
    modifiers = contract.modifiers().exec()

    for modifier in modifiers:
      result.append(modifier)

  return result
```

## Example output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "LTP",
  "sol_modifier": "modifier onlyOwner() {\n        require(owner() == _msgSender(),\"Ownable: caller is not the owner\");\n        _;\n    }"
}
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "LTP",
  "sol_modifier": "modifier onlyMinter() {\n        require(msg.sender == minter,'Sender is not the minter');\n        _;\n    }"
}
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "LTP",
  "sol_modifier": "modifier onlyMinterOrOwner() {\n        require( (msg.sender == minter) || (msg.sender == owner()),'Sender is not the minter nor owner');\n        _;\n    }"
}
```
