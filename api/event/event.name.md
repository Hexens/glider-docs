---
description: Returns the name of the event.
---

# Event.name

## Return type

→ str

## Example

```python
from glider import *
def query():
  # Find contracts with the suffix "ERC20"
  contracts = Contracts().name_suffix("ERC20").exec(100)

  contractsWithEvents = []
  for c in contracts:
    contract = {"name": c.name, "events": []}
    for event in c.events():
      contract["events"].append(event.name)

    # For each contract, return its name and the names of its events
    contractsWithEvents.append(contract)

  return contractsWithEvents
```

## Example output

```json
[
  {
    "name": "ERC20",
    "events": ["OwnershipTransferred", "Transfer", "Approval"]
  },
  {
    "name": "DelegateERC20",
    "events": [
      "OwnershipTransferred",
      "Transfer",
      "Approval",
      "Burn",
      "SetBurnBounds",
      "Blacklisted",
      "Mint"
    ]
  },
  ...
]
```
