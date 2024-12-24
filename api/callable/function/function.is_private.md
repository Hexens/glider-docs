---
description: >-
  Returns true if the visibility of the function is private, otherwise returns
  false.
---

# Function.is\_private()

`is_private() → bool`

## Example

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

## Output

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
