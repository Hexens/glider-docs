# Contract.address()

## Description

It returns the on-chain address of a Contract.

## Return type

str (e.g. `"0x798AcB51D8FBc97328835eE2027047a8B54533AD"`)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().with_name("ERC721").exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

## Example output

```json
{
  "addresses": [
    "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "0x27A05e7a40F2d980F8853e94c3cE54C70e68527D",
    "0x3450955Ffe1e8DE92c7348a497d7Fc2C9283ff3d",
    "0x961868ff892031fd3197AAC138e358b5983f59a8",
    "0x404bB1626E4e2EC681FDE0Bf6D3E36c1246B8173"
  ]
}
```
