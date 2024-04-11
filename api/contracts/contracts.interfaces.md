---
description: Adds a filter to the current query that gets contracts that are interfaces.
---

# Contracts.interfaces()

Input:

```python
from glider import *

def query():
  contracts = Contracts().interfaces().exec(1)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x798AcB51D8FBc97328835eE2027047a8B54533AD"
  ]
}
```
