---
description: Returns the values of the enum.
---

# Enum.values

_`property`_` ``value:`` `_`str`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 71)

    contract = contracts[0]
    
    for enum in contract.enums().exec():
      for enum_value in enum.values:
        print(enum_value)

    return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-25 at 6.32.13 PM.png" alt=""><figcaption></figcaption></figure>
