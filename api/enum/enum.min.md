---
description: Returns the minimum value of the enum.
---

# Enum.min

_`property`_` ``min:`` `_`int`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 166)
    i = 0
    contract = contracts[0]
    
    for enum in contract.enums().exec():
      print(enum.min)

    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "0"
    ]
  }
]
```
