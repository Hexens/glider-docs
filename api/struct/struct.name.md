---
description: Returns the name of the struct.
---

# Struct.name

_`property`_` ``name :`` `_`str`_

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
