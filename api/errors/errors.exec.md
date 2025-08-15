---
description: Executes the formed query and returns the list of Error objects.
---

# Errors.exec()

`exec(`_`limit_count: int = 0, offset_count: int = 0`_`) →` [`APIList`](../iterables/apilist.md)`[`[`Error`](../error/)`]`

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 2265)

  for contract in contracts:
    for error in contract.errors().exec():
      print(error.name)

  return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-29 at 6.21.15 PM.png" alt=""><figcaption></figcaption></figure>
