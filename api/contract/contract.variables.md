# Contract.variables()

## Description

Returns the list of all variables of the contract.

## Return type

[Variables](../variables/)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(10)
  
  names = []
  for contract in contracts:
    variables = contract.variables().exec()

    for variable in variables:
      names.append(variable.name())

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "_owner",
    "_name",
    "_symbol",
    "_owners",
    "_balances",
    "_tokenApprovals",
    "_operatorApprovals",
    "_tokenURIs",
    "owner",
    "paused",
    "canPause"
  ]
}
```
