---
description: Adds a filter to get contracts that have a struct with the given name.
---

# Contracts.with\_struct\_name()

`with_struct_name(name: str, sensitivity: bool = True) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():

  contracts = Contracts().with_struct_name("User").exec(100)

  # Return the first five functions
  return contracts[0:5]
```

## Output Example

```json
{
    {
        "contract":"0x99280cefeecceaf2c5b1537cd4eeb3b44c3c171f"
        "contract_name": "SmartWay"
    }
}
```

