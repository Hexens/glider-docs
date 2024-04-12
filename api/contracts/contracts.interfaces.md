---
description: Adds a filter to get contracts that are interface.
---

# Contracts.interface\_contracts()

## Function Signature

`interface_contracts() →` [`Contracts`](../contract/)

## Example Query

```python
from glider import *

def query():

  interface = Contracts().interface_contracts().exec(1)

  return interface
```

## Output Example

```json
{
    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
    "contract_name": "IERC20"
}
```
