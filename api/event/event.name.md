---
description: Returns the name of the event.
---

# Event.name

_`property`_` ``name:`` `_`str`_

## Example

```python
from glider import *


def query():
  # Find contracts with the suffix "ERC20"
  contracts = Contracts().with_name_suffix("ERC20").exec(100)

  for c in contracts:
    for event in c.events().exec():
      # For each contract's event, print the event name
      print(event.name)

  return []
```

## Example output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-14 at 1.45.08 PM (1).png" alt=""><figcaption></figcaption></figure>
