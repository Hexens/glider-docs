---
description: Adds a filter to get contracts with the given name.
---

# Contracts.with\_name()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_name("Account").exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```
{
  "addresses": [
    "0x3746F68ed3299948126a32E85b30c10C7F78109C",
    "0x546728A95FeDC9E5b98F27564873226a8f536D79",
    "0x2B2C387E2aAcD3bcFC77505aBFfd82DF172dE589",
    "0x4a483d1c3b7712daa0e6c1eeee979ae3e25d42d2",
    "0x2D8Be68bF59E6529466df26b311231E1BeaEB037"
  ]
}
```
