---
description: Returns true if the function has modifiers, otherwise returns false
---

# Function.has\_modifiers()

`has_modifiers() → bool`

## Example

```python
from glider import *

def query():
    functions_with_modifiers = (
      Functions()
      .exec(100)
      .filter(lambda x: x.has_modifiers())
    )

    return functions_with_modifiers
```

## Output

<figure><img src="../../../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

