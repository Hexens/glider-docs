---
description: Executes the formed query and returns the list of Struct objects.
---

# Structs.exec()

`exec(`_`limit_count: int = 0, offset_count: int = 0`_`) →` [`APIList`](../iterables/apilist.md)`[`[`Struct`](../struct/)`]`

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 26)

  for struct in contracts[0].structs().exec():
    print(struct.name)

  return []
```

## Example Output

```json
[
  {
    "print_output": [
      "UserInfo"
    ]
  }
]
```
