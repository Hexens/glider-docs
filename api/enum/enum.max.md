---
description: Returns the maximum value of the enum.
---

# Enum.max

_`property`_` ``max:`` `_`int`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 71)

    for enum in contracts[0].enums().exec():
      print(enum.max)

    return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-25 at 6.22.46 PM.png" alt=""><figcaption></figcaption></figure>
