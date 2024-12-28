---
description: Returns true if the function is global, otherwise returns false.
---

# Function.is\_global()

`is_global() → bool`

## Example

```python
from glider import *

def query():
    global_functions = (
      Functions()
      .exec(30_000)
      .filter(lambda x: x.is_global())
    )

    return global_functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
