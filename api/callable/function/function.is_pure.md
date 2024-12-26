---
description: Returns true if the function is pure, otherwise returns false.
---

# Function.is\_pure()

`is_pure() → bool`

## Example

```python
from glider import *

def query():
    pure_functions = (
      Functions()
      .exec(100)
      .filter(lambda x: x.is_pure())
    )

    return pure_functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
