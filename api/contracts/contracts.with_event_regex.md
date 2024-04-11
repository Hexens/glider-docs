---
description: >-
  Adds a filter to get contracts that have an event whose name matches the given
  regex.
---

# Contracts.with\_event\_regex()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_event_regex('^Update.*').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0xeB3D8DBFa30A83A80DcFd5F6317426a6ce41CEE4",
    "0xb2F7E60359438655311e6582dfb2f9EF04CB142C",
    "0xb2F7E60359438655311e6582dfb2f9EF04CB142C",
    "0x7FAfB0571B10757373df3c463C472C39D688711c",
    "0x7e6B034880393a4604175D6867ba25Fa16402E43"
  ]
}
```
