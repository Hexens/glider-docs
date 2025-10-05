---
description: Returns the type of the struct field.
---

# StructField.type

_`property`_` ``type :`` `_`Type`_

## Query Example

```python
from glider import *


def query():
  contracts = Contracts().with_name("DefaultReserveInterestRateStrategy").exec(1)

  for contract in contracts:
    for struct in contract.structs().exec():
      for struct_field in struct.fields:
        print(struct_field.type)

  return contracts
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-10 at 5.40.57 PM.png" alt=""><figcaption></figcaption></figure>
