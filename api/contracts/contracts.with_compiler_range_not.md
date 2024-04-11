---
description: >-
  Adds a filter to get contracts whose compilation version isn't in the given
  range.
---

# Contracts.with\_compiler\_range\_not()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_compiler_range_not("0.8.0", "0.8.20").exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23",
    "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23",
    "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23",
    "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23",
    "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23"
  ]
}
```
