---
description: Adds a filter to get contracts that names have the given suffix.
---

# Contracts.name\_suffix()

Input:

```python
from glider import *

def query():
  contracts = Contracts().name_suffix("pool").exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0xd73969Ba8aB79Fc3b4c70616671F65E5cA84C741",
    "0xCbFD6c51FbD6c1EA233CdCE42e5233Cc0CB6b833",
    "0xCbFD6c51FbD6c1EA233CdCE42e5233Cc0CB6b833",
    "0x1d346f3b23ad568608bc301fe9707c5320ce4c64"
  ]
}
```
