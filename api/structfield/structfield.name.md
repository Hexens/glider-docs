---
description: Returns the name of the struct field.
---

# StructField.name

_`property`_` ``name :`` `_`str`_

## Query Example

```python
from glider import *


def query():
  contracts = Contracts().with_name("DefaultReserveInterestRateStrategy").exec(1)

  for contract in contracts:
    for struct in contract.structs().exec():
      for struct_field in struct.fields:
        print(struct_field.name)

  return contracts
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-10 at 5.39.46 PM.png" alt=""><figcaption></figcaption></figure>
