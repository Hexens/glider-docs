---
description: >-
  Adds a filter to get contracts that have an event whose name has the given
  prefix.
---

# Contracts.with\_event\_prefix()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_event_prefix('user').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x84efEf0c34698d29014a1d7bcEBcBBCcb91b2865",
    "0xdd4e308c42ebc152c53172ae70e0ab1aee95d67d",
    "0xdd4e308c42ebc152c53172ae70e0ab1aee95d67d",
    "0xdd4e308c42ebc152c53172ae70e0ab1aee95d67d",
    "0xdd4e308c42ebc152c53172ae70e0ab1aee95d67d"
  ]
}
```
