---
description: >-
  Returns a list of all internal call instructions if the parameter is skipped.
  Otherwise, returns call instructions of corresponding type (internal, public
  or private)
---

# Instructions.internal\_calls()

`internal_calls(visibility: str = '') →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return Instructions().internal_calls().exec(3,3)
```

## Example Output

<figure><img src="../../.gitbook/assets/image (254).png" alt=""><figcaption></figcaption></figure>
