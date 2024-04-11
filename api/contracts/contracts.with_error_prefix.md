---
description: >-
  Adds a filter to get contracts that have an error whose name has the given
  prefix.
---

# Contracts.with\_error\_prefix()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_error_prefix("_er").exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0xbe90c8e5b01669188978D6CF6d39324ab5410ccf",
    "0x5985B9a914bCd6A46d72690Df78c1640064c499e",
    "0x5985B9a914bCd6A46d72690Df78c1640064c499e",
    "0x5985B9a914bCd6A46d72690Df78c1640064c499e",
    "0x5985B9a914bCd6A46d72690Df78c1640064c499e"
  ]
}
```
