---
description: >-
  Returns Contracts object for the contracts which were derived from the
  contract.
---

# Contract.derived\_contracts()



## Return type

[Contracts](../contracts/)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1)
  
  names = []
  for contract in contracts:
    derived_contracts = contract.derived_contracts().exec()

    for contract in derived_contracts:
      names.append(contract.name)

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "ERC721",
    "ERC721URIStorage",
    "LTP",
    "Ownable"
  ]
}
{
  "print_output": [
    "Context"
  ]
}
```
