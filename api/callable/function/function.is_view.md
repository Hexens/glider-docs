---
description: Returns true if the function is view, otherwise returns false.
---

# Function.is\_view()

`is_view() → bool`

## Example

```python
from glider import *

def query():
    view_functions = (
      Functions()
      .exec(100)
      .filter(lambda x: x.is_view())
    )

    return view_functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>
