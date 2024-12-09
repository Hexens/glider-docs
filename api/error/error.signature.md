---
description: Returns the signature of the error.
---

# Error.signature

_`property`_` ``signature :`` `_`str`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 1336)

  for contract in contracts:
    for error in contract.errors().exec():
      print(error.signature)

  return []
```

## Example Output

```json
[
  {
    "print_output": [
      "OnlySimulatedBackend()"
    ]
  }
]
```
