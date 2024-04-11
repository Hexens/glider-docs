---
description: >-
  Adds a filter to get contracts that have an event whose name has the given
  suffix.
---

# Contracts.with\_event\_suffix()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_event_suffix('debt').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x1A1288c4eF9beE001177fEc4d0Fc3Ed2cdF23A3a",
    "0x069B70079fAC1ffC1A6F3d3c4724d0f5dA03D953",
    "0x8eAA1477dfC21671dC42B9F13ACe4F54616882b0",
    "0x070f7ee9dfB8dc4E14356799D06DdA50518efb3C",
    "0x9dE22166620D7e1984462582f12eeF059fC9a673"
  ]
}
```
