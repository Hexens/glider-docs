---
description: Returns the source code of the event.
---

# Event.source\_code()

`source_code() → str`

## Query Example

```python
from glider import *


def query():
  # Find contracts with the suffix "ERC20"
  contracts = Contracts().with_name_suffix("ERC20").exec(100)

  for c in contracts:
    for event in c.events().exec():
      # For each contract's event, print the event address
      print(event.source_code())

  return []
```

## Output Example

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-14 at 1.46.50 PM.png" alt=""><figcaption></figcaption></figure>
