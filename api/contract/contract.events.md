---
description: The function returns all the events of a Contract.
---

# Contract.events()

`events() →` [`APIList`](../iterables/apilist.md)`[`[`Event`](../event/)`]`

## Example query

```python
from glider import *

def query():
    contracts = Contracts().exec(2)
   
    for contract in contracts:
        events = contract.events()

    for event in events:
        print(event.name)

    return contracts
```

## &#x20;Output Example

```json
[
  ...
  {
    "print_output": [
      "Transfer",
      "Approval",
      "Burn",
      "OwnershipTransferred"
    ]
  }
]
```
