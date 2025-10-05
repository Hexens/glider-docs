---
description: Returns the fields of the struct.
---

# Struct.fields

_`property`_` ``fields :` [_`APIList`_](../iterables/apilist.md)_`[`_[_`StructField`_](../structfield/)_`]`_

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

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-10 at 5.33.42 PM.png" alt=""><figcaption></figcaption></figure>
