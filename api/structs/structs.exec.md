---
description: Executes the formed query and returns the list of Struct objects.
---

# Structs.exec()

`exec(`_`limit_count: int = 0, offset_count: int = 0`_`) →` [`APIList`](../iterables/apilist.md)`[`[`Struct`](../struct/)`]`

## Query Example

```python
from glider import *


def query():
  contracts = Contracts().with_name("DefaultReserveInterestRateStrategy").exec(1)

  for contract in contracts:
    for struct in contract.structs().exec():
      print(struct.name)

  return contracts
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-10 at 5.43.41 PM.png" alt=""><figcaption></figcaption></figure>
