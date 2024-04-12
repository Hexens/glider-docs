---
description: Executes the formed query and returns the list of Contract objects.
---

# Contracts.exec()

## Function Signature

`exec(limit_count: int = 0, offset_count: int = 0) -> List[`[`Contract`](../contract/)`]`

## Example Query

```python
from glider import *

def query():
  contracts = Contracts().exec(2)

  return contracts
```

## Output Example

```json
{
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Context"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable"
    }
}
```
