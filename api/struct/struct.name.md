---
description: Returns the name of the struct.
---

# Struct.name

_`property`_` ``name :`` `_`str`_

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

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-10 at 5.35.44 PM.png" alt=""><figcaption></figcaption></figure>
