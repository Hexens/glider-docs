# Contract.chain\_id()

## Description

Returns the ID of the blockchain where a Contract was deployed.

## Return type

int (e.g., 1 for Ethereum)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().with_name("ERC721").exec(5)
  
  chain_ids = []
  for contract in contracts:
    chain_ids.append(contract.chain_id())

  return [{"chain_ids": chain_ids}]
```

## Example output

```json
{
  "chain_ids": [
    69,
    69,
    69,
    69,
    69
  ]
}
```
