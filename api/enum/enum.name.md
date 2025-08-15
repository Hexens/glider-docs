---
description: Returns the name of the enum.
---

# Enum.name

_`property`_` ``name:`` `_`str`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 71)

    for enum in contracts[0].enums().exec():
      print(enum.name)

    return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-25 at 6.24.51 PM.png" alt=""><figcaption></figcaption></figure>
