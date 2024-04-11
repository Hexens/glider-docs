# Contract.dump\_into\_json()

## Description

It returns the internal technical information about a Contract.

## Return type

```json
{
    "name": string
    "relative_filepath": string
}
```

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1)
  
  jsons = []
  for contract in contracts:
    json = contract.dump_into_json()
    jsons.append(json)

  return jsons
```

## Example output

```json
{
  "name": "Context",
  "relative_filepath": "../smart-contract-sanctuary-ethereum/contracts/kovan/79/798AcB51D8FBc97328835eE2027047a8B54533AD_LTP.sol"
}
```
