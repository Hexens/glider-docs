---
description: Returns a serialized JSON object of the event.
---

# Event.dump\_into\_json()

## Return type

→ Dict

## Example

```python
from glider import *
def query():
  # Find contracts with an event called "Transfer"
  contracts = Contracts().with_event_name('Transfer').exec(100)

  transferEventsObjs = []
  for contract in contracts:
    for event in contract.events():
      if event.name == "Transfer":
        # Return the JSON serialized representation of each "Transfer" event in every single contract
        transferEventsObjs.append(event.dump_into_json())

  return transferEventsObjs
```

## Example output

```json
[
  {
    "signature": "Transfer(address,address,uint256)",
    "name": "Transfer",
    "args": [
      {
        "name": "from",
        "type": "address",
        "indexed": true
      },
      {
        "name": "to",
        "type": "address",
        "indexed": true
      },
      {
        "name": "tokenId",
        "type": "uint256",
        "indexed": true
      }
    ]
  },
  ...
]
```
