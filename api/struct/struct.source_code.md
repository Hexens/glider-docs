---
description: Returns the source code of the struct.
---

# Struct.source\_code()

## Query Example

```python
from glider import *


def query():
  contracts = Contracts().with_name("DefaultReserveInterestRateStrategy").exec(1)

  for contract in contracts:
    for struct in contract.structs().exec():
      print(struct.source_code())

  return contracts
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-10 at 5.37.45 PM.png" alt=""><figcaption></figcaption></figure>
