---
description: Adds a filter to get functions/modifiers associated with the given address.
---

# Callables.with\_address()

## Query Example

```python
from glider import *


def query():
    functions = (
        Functions()
        .with_name("swapTokens")
        .with_address("0x4186829914d1b7b130b5153f4aabd21142e8e658")
        .exec(1)
    )

    return functions
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-17 at 1.06.56 PM.png" alt=""><figcaption></figcaption></figure>
