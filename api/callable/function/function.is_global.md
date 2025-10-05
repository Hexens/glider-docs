---
description: Returns true if the function is global, otherwise returns false.
---

# Function.is\_global()

`is_global() → bool`

## Query Example

```python
from glider import *

def query():
    global_functions = (
      Functions()
      .exec(85_200)
      .filter(lambda x: x.is_global())
    )

    return global_functions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-15 at 2.58.32 PM.png" alt=""><figcaption></figcaption></figure>
