---
description: Returns arguments' types of the event.
---

# Event.arg\_list()

`arg_list() → List[str]`

## Example query

```python
from glider import *


def query():
  # Find contracts with an event called "Transfer"
  contracts = Contracts().with_event_name('Transfer').exec(100)

  for contract in contracts:
    for event in contract.events().exec():
      if event.name == "Transfer":
        # For each "Transfer" event in every single contract, print its arguments
        print(event.arg_list())

  return []
```

## Output Example

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-14 at 1.45.08 PM.png" alt=""><figcaption></figcaption></figure>
