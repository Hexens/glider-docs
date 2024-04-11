---
description: Returns arguments' types of the event.
---

# Event.arg\_list()

## Return type

→ List\[str]

## Example

```python
from glider import *
def query():
  # Find contracts with an event called "Transfer"
  contracts = Contracts().with_event_name('Transfer').exec(100)

  transferEventsArgs = []
  for contract in contracts:
    for event in contract.events():
      if event.name == "Transfer":
        # For each "Transfer" event in every single contract, return its arguments
        transferEventsArgs.append(event.arg_list())

  return transferEventsArgs
```

## Example output

```json
[
  ["address", "address", "uint256"],
  ["address", "address", "uint256"],
  ...
]
```
