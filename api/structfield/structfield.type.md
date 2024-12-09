---
description: Returns the type of the struct field.
---

# StructField.type

_`property`_` ``type :`` `_`Type`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 26)

  for struct in contracts[0].structs().exec():
    for struct_field in struct.fields:
      print(struct_field.type)

  return []
```

## Example Output

```json
[
  {
    "print_output": [
      "uint256",
      "uint256",
      "bool"
    ]
  }
]
```
