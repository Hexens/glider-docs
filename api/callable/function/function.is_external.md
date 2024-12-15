---
description: >-
  Returns true if the visibility of the function is external, otherwise returns
  false.
---

# Function.is\_external()

`is_external() → bool`

## Example

```python
from glider import *

def query():
    external_functions = (
      Functions()
      .exec(10, 100)
      .filter(lambda x: x.is_external())
    )

    return external_functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>
