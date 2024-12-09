---
description: Returns the data of the struct.
---

# Struct.data

_`property`_` ``data :`` `_`Dict`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 26)

  for struct in contracts[0].structs().exec():
    print(struct.data)

  return []
```

## Example Output

```json
[
  {
    "print_output": [
      "{
        '_key': 'caf2be195cea94c92ba1b8dc8c9da541', 
        '_id': 'structs/caf2be195cea94c92ba1b8dc8c9da541', 
        '_rev': '_iaelySK--_', 
        'name': 'UserInfo', 
        'fields': [
          {
            'name': 'amount', 
            'type': {
              'type': 'elementary', 
              'name': 'uint256'
            }
          }, {
            'name': 'rewardDebt', 
            'type': {
              'type': 'elementary', 
              'name': 'uint256'
            }
          }, {
            'name': 'registrated', 
            'type': {
              'type': 'elementary', 
              'name': 'bool'
            }
          }
        ], 
        'relative_filepath': '0xe5fA13058EdE558a2bFA675043f175148858A5F6_StakeMaster.sol'
      }"
    ]
  }
]
```
