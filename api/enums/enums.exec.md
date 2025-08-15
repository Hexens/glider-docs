---
description: Executes the formed query and returns the list of Enum objects.
---

# Enums.exec()

`exec(`_`limit_count: int = 0, offset_count: int = 0`_`) →` [`APIList`](../iterables/apilist.md)`[`[`Enum`](../enum/)`]`

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 71)

  for contract in contracts:
    for enum in contract.enums().exec():
      print(enum.name)
  
  return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-25 at 6.33.58 PM.png" alt=""><figcaption></figcaption></figure>
