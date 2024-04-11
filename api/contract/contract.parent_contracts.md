# Contract.parent\_contracts()

## Description

Returns Contracts object for the contracts from which the contract was inherited directly.

## Return type

[Contracts](../contracts/)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 1)
  
  names = []
  for contract in contracts:
    print(contract.name)

    parent_contracts = contract.parent_contracts().exec()

    for contract in parent_contracts:
      names.append(contract.name)

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "Context"
  ]
}
{
  "print_output": [
    "Ownable"
  ]
}
```
