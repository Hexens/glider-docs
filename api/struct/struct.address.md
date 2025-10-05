---
description: Returns the address of the struct.
---

# Struct.address

`property address: str`

## Query Example

```python
from glider import *


def query():
  contracts = Contracts().with_name("DefaultReserveInterestRateStrategy").exec(1)

  for contract in contracts:
    for struct in contract.structs().exec():
      print(struct.address)

  return contracts
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-10 at 5.03.49 PM.png" alt=""><figcaption></figcaption></figure>
