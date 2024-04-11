---
description: Adds a filter to get contracts that have an error with the given signature.
---

# Contracts.with\_error\_signature()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_error_signature('Unauthorized()').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x4aaa25B1972Bb72266E67F7E146b9EBED63490Ad",
    "0x97e121ecdcf554f60857e5dc39ed1ea14337d506",
    "0x97e121ecdcf554f60857e5dc39ed1ea14337d506",
    "0x7c5eF576dd7fd87C639b330dA4C854EA05ABe12E",
    "0x9E87F43Dec627E6d55211b0d66686eBe5B14B65B"
  ]
}
```
