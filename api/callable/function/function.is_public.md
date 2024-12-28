---
description: >-
  Returns true if the visibility of the function is public, otherwise returns
  false.
---

# Function.is\_public()

`is_public() → bool`

## Example

```python
from glider import *

def query():
    public_functions = (
      Functions()
      .exec(10)
      .filter(lambda x: x.is_public())
    )

    return public_functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
