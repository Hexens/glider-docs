---
description: Adds a filter to get contracts that are not interface.
---

# Contracts.non\_interface\_contracts()

## Function Signature

`non_interface_contracts() ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():

  non_interface_contracts = Contracts().non_interface_contracts().exec(3)

  return non_interface_contracts
```

## Output Example

```json
{
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "Context"
    },
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "SafeMath"
    },
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "Ownable"
    }
}
```
