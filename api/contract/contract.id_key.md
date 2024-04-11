# Contract.id\_key()

## Description

Returns the internal database id of a Contract.

## Return type

str (e.g., `"contracts/0f8238c5710c12f0046179755d932ad8"`)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(10)
  
  ids = []
  for contract in contracts:
    id = contract.id_key()
    ids.append(id)

  return [{"ids": ids}]
```

## Example output

```json
{
  "ids": [
    "contracts/3caf682820e2d2f350926c66496dd80a",
    "contracts/daad7bef47df9ac01c6cc3422ff4ebee",
    "contracts/0f8238c5710c12f0046179755d932ad8",
    "contracts/a970a857180935b6af57cf9f3a133dfb",
    "contracts/e61ec71ef5cc345e7f44714c6139349a",
    "contracts/2fc4420c9645e974eeb9563c6f1e2c0e",
    "contracts/0102f35300168a508d759b6bbc319333",
    "contracts/c7f7215abb1ce81a77e28b320ab38636",
    "contracts/1c880e636e52dcfab06b750e8961ae13",
    "contracts/fd81371a5e8c15aec848035ec5d0528e"
  ]
}
```
