---
description: Adds a filter to get contracts that have an event with the given signature.
---

# Contracts.with\_event\_signature()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_event_signature('Deposit()').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0xfb1FED416758326CdeBE673c0E12c287C1e91198",
    "0x7bc20d6137750189dd6cf5e92d92ea74786f520f",
    "0x9a02B92718844E2D285FC278529653D499d29827",
    "0x538378bbc847b297ec125600326b80dfcbd6ce08",
    "0x2c4a10070595b386503f7165d6d6d0d762275e73"
  ]
}
```
