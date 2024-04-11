---
description: Adds a filter to get contracts that have an event with the given name.
---

# Contracts.with\_event\_name()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_event_name('transfer').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x5f3d950617cfb119bc1e6867594e63ca86aedc5b",
    "0xece7ff5350949a396d02963459e8bd088fff80db",
    "0x76adb19cc6b2565f586c78e945a886f9b954861f",
    "0x1d0105bbb80b2d05789c668995762d02fd5681e1",
    "0xAe7068A433D37d3416000b0733A5b5e6Fac7Bf69"
  ]
}
```
