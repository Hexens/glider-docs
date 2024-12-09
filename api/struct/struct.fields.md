---
description: Returns the fields of the struct.
---

# Struct.fields

_`property`_` ``fields :` [_`APIList`_](../iterables/apilist.md)_`[`_[_`StructField`_](../structfield/)_`]`_

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
