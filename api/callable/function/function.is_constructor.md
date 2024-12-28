---
description: Returns true if the function is constructor, otherwise returns false.
---

# Function.is\_constructor()

`is_constructor() → bool`

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

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
