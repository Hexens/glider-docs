---
description: Returns the source code of the enum.
---

# Enum.source\_code()

`source_code() → str`

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 95)

    for enum in contracts.enums().exec():
      print(enum.source_code())

    return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-25 at 6.30.39 PM.png" alt=""><figcaption></figcaption></figure>
