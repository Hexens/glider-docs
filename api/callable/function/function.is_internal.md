---
description: >-
  Returns true if the visibility of the function is internal, otherwise returns
  false.
---

# Function.is\_internal()

`is_internal() → bool`

## Example

```python
from glider import *

def query():
    internal_functions = (
      Functions()
      .exec(20)
      .filter(lambda x: x.is_internal())
    )

    return internal_functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
