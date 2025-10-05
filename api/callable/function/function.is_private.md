---
description: >-
  Returns true if the visibility of the function is private, otherwise returns
  false.
---

# Function.is\_private()

`is_private() → bool`

## Query Example

```python
from glider import *

def query():
    private_functions = (
      Functions()
      .exec(20)
      .filter(lambda x: x.is_private())
    )

    return private_functions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-15 at 3.00.38 PM.png" alt=""><figcaption></figcaption></figure>
