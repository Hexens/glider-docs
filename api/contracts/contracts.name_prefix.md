---
description: Adds a filter to get contracts whose names have the given prefix.
---

# Contracts.name\_prefix()

Input:

```python
from glider import *

def query():
  contracts = Contracts().name_prefix("test").exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0xa66ab394d86d5b6af4815a570513b1c813c9152c",
    "0xb67e972bff8df12bf76c45d322bdee31d5964223",
    "0xcc6a7d2a7e23f39dbea3718ebdc0feb68959ac68",
    "0x37aB40366C27AF9F95d36Dd7c4eEFa4EcB2D9e50",
    "0x97147E71a7a49F1f4dB4fA5b68316c0eC327B792"
  ]
}
```
