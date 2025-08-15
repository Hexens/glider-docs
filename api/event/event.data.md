---
description: Returns the data of the event.
---

# Event.data

_`property`_` ``data:`` `_`Dict`_

## Example query

```python
from glider import *


def query():
  # Find contracts with an event called "Transfer"
  contracts = Contracts().with_event_name('Transfer').exec(1)

  for contract in contracts:
    for event in contract.events().exec():
      if event.name == "Transfer":
        # For each "Transfer" event in every single contract, return its data
        print(event.data)

  return []
```

## Output Example

Example output of event data:

```json
{
    '_key': '82fac7da92cf739a6ee2c8b9622dae09', 
    '_id': 'events/82fac7da92cf739a6ee2c8b9622dae09', 
    '_rev': '_jw0UR2----', 
    'name': 'Transfer', 
    'signature': 'Transfer(address,address,uint256)', 
    'selector': 3723645613, 
    'args': [
        {
            'name': 'from', 
            'type': {
                'type': 'elementary', 
                'name': 'address'
            }, 
            'indexed': True
        }, {
            'name': 'to', 
            'type': {
                'type': 'elementary', 
                'name': 'address'
            }, 
            'indexed': True
        }, {
            'name': 'rawAmt', 
            'type': {
                'type': 'elementary', 
                'name': 'uint256'
            }, 
            'indexed': False
        }
    ], 
    'relative_filepath': '0x956ba4b0a0ad5642d39be1ac87eab1af2863fcca_Datagold.sol', 
    'first_source_line': 29, 
    'last_source_line': 29, 
    'start_column': 5, 
    'end_column': 73, 
    'address': '0x956ba4b0a0ad5642d39be1ac87eab1af2863fcca'
}
```
