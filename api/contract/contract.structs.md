# Contract.structs()

## Description

Returns the list of all structs of the contract.

## Return type

List\[Struct]

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(50, 50)
  
  names = []
  for contract in contracts:
    structs = contract.structs()

    for struct in structs:
      names.append(struct.name)

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "TData",
    "TokenInfo",
    "MintParams",
    "PoolInfo",
    "TrancheInfo",
    "PoolSlice",
    "SliceInfo",
    "ApplyResult",
    "CollateralConfig",
    "Vault",
    "CollateralConfig"
  ]
}
```
