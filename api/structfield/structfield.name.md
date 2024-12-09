---
description: Returns the name of the struct field.
---

# StructField.name

_`property`_` ``name :`` `_`str`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 26)

  for struct in contracts[0].structs().exec():
    for struct_field in struct.fields:
      print(struct_field.name)

  return []
```

## Example Output

```json
[
  {
    "print_output": [
      "amount",
      "rewardDebt",
      "registrated"
    ]
  }
]
```
