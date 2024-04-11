# Contract.enums()

## Description

The function returns all the enums of a Contract.

## Return type

List\[Enum]

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(100)
  
  names = []
  for contract in contracts:
    enums = contract.enums()

    for enum in enums:
      names.append(enum.name)

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "Upgradability",
    "Tranches"
  ]
}
```
