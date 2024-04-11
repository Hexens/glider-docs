---
description: Adds a filter to get contracts that have a struct with the given fields count.
---

# Contracts.with\_struct\_fields\_count()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_struct_fields_count(7).exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0xE1e65E4be161950eb18185703cFCacB35c4c65B3",
    "0xe90baa4A5fD4fE25443d27e6E2883350a0E67855",
    "0xb51Da721B77Db063B02b79D7e79558b9C2e34Ea6",
    "0x2307316e1846CaBf740f9bea0F8Aa0E4cb82b89c",
    "0x139D12963897129D48C99402Cc481e8C0E8FD0BC"
  ]
}
```
