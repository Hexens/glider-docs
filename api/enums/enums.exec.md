---
description: Executes the formed query and returns the list of Enum objects.
---

# Enums.exec()

`exec(`_`limit_count: int = 0, offset_count: int = 0`_`) →` [`APIList`](../iterables/apilist.md)`[`[`Enum`](../enum/)`]`

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 357)

  for contract in contracts:
    for enum in contract.enums().exec():
      print(enum.name)
  
  return []
```

## Example Output

```json
[
  {
    "print_output": [
      "States",
      "MessageStatus"
    ]
  }
]
```
