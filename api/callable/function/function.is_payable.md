---
description: Returns true if the function is payable, otherwise returns false.
---

# Function.is\_payable()

`is_payable() → bool`

## Example

```python
from glider import *

def query():
    payable_functions = (
      Functions()
      .exec(1000)
      .filter(lambda x: x.is_payable())
    )

    return payable_functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>
