---
description: Returns the address of the enum.
---

# Enum.address

_`property`_` ``address:`` `_`str`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 71)

    for enum in contracts[0].enums().exec():
      print(enum.address)

    return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-25 at 5.10.34 PM.png" alt=""><figcaption></figcaption></figure>
