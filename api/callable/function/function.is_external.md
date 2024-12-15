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
    constructors = (
      Functions()
      .exec(100)
      .filter(lambda x: x.is_constructor())
    )

    return constructors
```

## Output

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
