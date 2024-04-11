---
description: Adds a filter to get contracts that don't have the given name.
---

# Contracts.with\_name\_not()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_name_not("Account").exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```
{
  "addresses": [
    "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "0x798AcB51D8FBc97328835eE2027047a8B54533AD"
  ]
```

