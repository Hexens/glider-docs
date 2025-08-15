---
description: Returns the signature of the event.
---

# Event.signature

_`property`_` ``signature:`` `_`str`_

## Example

```python
from glider import *


def query():
  # Find contracts with the suffix "ERC20"
  contracts = Contracts().with_name_suffix("ERC20").exec(100)

  for c in contracts:
    for event in c.events().exec():
      # For each contract's events, print the event signature
      print(event.signature)

  return []
```

## Example output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-14 at 1.46.31 PM.png" alt=""><figcaption></figcaption></figure>
