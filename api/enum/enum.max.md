---
description: Returns the maximum value of the enum.
---

# Enum.max

_`property`_` ``max:`` `_`int`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 166)
    i = 0
    contract = contracts[0]
    
    for enum in contract.enums().exec():
      print(enum.max)

    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "4"
    ]
  }
]
```
