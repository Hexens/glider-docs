---
description: Adds a filter to get contracts that have a struct with the given field name.
---

# Contracts.with\_struct\_field\_name()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_struct_field_name('balance').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output (\~80 secs):

```python
{
  "addresses": [
    "0xe90baa4A5fD4fE25443d27e6E2883350a0E67855",
    "0x139D12963897129D48C99402Cc481e8C0E8FD0BC",
    "0x139D12963897129D48C99402Cc481e8C0E8FD0BC",
    "0xea10031Bb69b1b64B19447C7a956f9a951183fb5",
    "0x0CB65c3B85F730E08C31bdf67a948f64847EB7CA"
  ]
}
```
