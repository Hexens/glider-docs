---
description: Adds a filter to get contracts that don't have the given name.
---

# Contracts.with\_name\_not()

## Function Signature

`with_name_not(name: str, sensitivity: bool = True) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_name_not("Context").exec(1)

  return contracts
```

## Output Example

```json
{
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "IERC20"
    }
}
```

