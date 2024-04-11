---
description: Adds a filter to get contracts that are main
---

# Contracts.mains()

Input:

```python
from glider import *

def query():
  contracts = Contracts().mains().exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
    "0x854f8aa8fc54cc57e9ab86318d498511342ff9d8",
    "0x561ae3768ee95987b355c287f985f2838f01e632",
    "0x27A05e7a40F2d980F8853e94c3cE54C70e68527D"
  ]
}
```
