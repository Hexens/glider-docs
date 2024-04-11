---
description: Adds a filter to get contracts whose names match the given regex.
---

# Contracts.name\_regex()

Input:

```python
from glider import *

def query():
  contracts = Contracts().name_regex('^pool.*').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x94a17586A22ddccBBBe3e618184DecD15BB227fA",
    "0x94a17586A22ddccBBBe3e618184DecD15BB227fA",
    "0x94a17586A22ddccBBBe3e618184DecD15BB227fA",
    "0x8df9084935c4895d854b51cfc36cc9bb44114a7e",
    "0xfff78048519be8561f500f69e07a6eab807b4a11"
  ]
}
```
