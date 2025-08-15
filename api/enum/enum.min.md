---
description: Returns the minimum value of the enum.
---

# Enum.min

_`property`_` ``min:`` `_`int`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 71)

    for enum in contracts[0].enums().exec():
      print(enum.min)

    return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-25 at 6.24.09 PM.png" alt=""><figcaption></figcaption></figure>
