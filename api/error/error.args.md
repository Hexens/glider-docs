---
description: Returns the list of arguments of the error.
---

# Error.args

_`property`_` ``args:`` `_`List[Dict]`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 466)

  for contract in contracts:
    for error in contract.errors().exec():
      print(error.args)

  return []
```

## Example Output

```json
[
  {
    "print_output": [
      "[
        {
          'type': {
            'type': 'elementary', 
            'name': 'address'
          }, 
          'name': 'addr'
        }, {
          'type': {
            'type': 'elementary', 
            'name': 'uint256'
          }, 
          'name': 'balance'
        }
      ]"
    ]
  }
]
```
