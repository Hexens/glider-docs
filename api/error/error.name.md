---
description: Returns the name of the error.
---

# Error.name

_`property`_` ``name :`` `_`str`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 1336)

  for contract in contracts:
    for error in contract.errors().exec():
      print(error.name)

  return []
```

## Example Output

```json
[
  {
    "print_output": [
      "OnlySimulatedBackend"
    ]
  }
]
```
