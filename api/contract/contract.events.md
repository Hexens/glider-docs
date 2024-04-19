---
description: The function returns all the events of a Contract.
---

# Contract.events()

`events() → List[Event]`

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(5)
  
  names = []
  for contract in contracts:
    events = contract.events()

    for event in events:
      names.append(event.name)

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "OwnershipTransferred",
    "Transfer",
    "Approval",
    "ApprovalForAll"
  ]
}
```
