---
description: Executes the formed query and returns the list of Contract objects.
---

# Contracts.exec()

`exec(limit_count: int = 0, offset_count: int = 0) -> List[`[`Contract`](../contract/)`]`

## Example Query 1

```python
from glider import *

def query():
  contracts = Contracts().exec(3)

  return contracts
```

## Output Example 1

```json
{
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "Context"
    },
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "IERC20"
    },
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "SafeMath"
    }
}
```

## Example Query 2

```python
from glider import *

def query():

  contracts = Contracts().exec(1, 2)

  return contracts
```

## Output Query 2

```json
{
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "SafeMath"
    }
}
```
