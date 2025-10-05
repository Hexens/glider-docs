---
description: Adds a filter to get contracts associated with the given address.
---

# Contracts.with\_address()

## Query Example

```python
from glider import *


def query():
    return (
        Contracts()
        .with_address("0xdbEea69930D24988091b59f73B7898e7b0E9406F")
        .exec(1)
    )
    
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-17 at 12.49.44 PM.png" alt=""><figcaption></figcaption></figure>
