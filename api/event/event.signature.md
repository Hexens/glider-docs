---
description: Returns the signature of the event.
---

# Event.signature

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
      contract["events"].append(event.signature)

    # For each contract, return its name and the signatures of its events
    contractsWithEvents.append(contract)

  return contractsWithEvents
```

## Example output

```json
[
  {
    "name": "ERC20",
    "events": [
      "OwnershipTransferred(address,address)",
      "Transfer(address,address,uint256)",
      "Approval(address,address,uint256)"
    ]
  },
  {
    "name": "DelegateERC20",
    "events": [
      "OwnershipTransferred(address,address)",
      "Transfer(address,address,uint256)",
      "Approval(address,address,uint256)",
      "Burn(address,uint256)",
      "SetBurnBounds(uint256,uint256)",
      "Blacklisted(address,bool)",
      "Mint(address,uint256)"
    ]
  },
  ...
]
```
