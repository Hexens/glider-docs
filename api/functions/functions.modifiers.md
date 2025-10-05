---
description: Returns the Modifiers object for the modifiers of the function.
---

# Functions.modifiers()

`modifiers() →` [`Modifiers`](../callables/modifiers/)

## Query Example

```python
from glider import *


def query():
    modifiers = (
        Functions()
        .with_name("swapTokens")
        .modifiers()
        .exec(5)
    )
 
    return modifiers
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-17 at 1.14.09 PM.png" alt=""><figcaption></figcaption></figure>
