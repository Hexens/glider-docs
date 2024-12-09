---
description: Returns the name of the enum.
---

# Enum.name

_`property`_` ``name:`` `_`str`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 166)
    i = 0
    contract = contracts[0]
    
    for enum in contract.enums().exec():
      print(enum.name)

    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "RecoverError"
    ]
  }
]
```
