---
description: >-
  Returns true if the visibility of the function is external, otherwise returns
  false.
---

# Function.is\_external()

`is_external() → bool`

## Query Example

```python
from glider import *

def query():
    external_functions = (
      Functions()
      .exec(100)
      .filter(lambda x: x.is_external())
    )

    return external_functions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-15 at 2.48.19 PM.png" alt=""><figcaption></figcaption></figure>
