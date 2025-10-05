---
description: Adds a filter to get Instructions that call a function with the given name.
---

# Instructions.with\_callee\_name()

`with_callee_name(name: str, sensitivity: bool = True) →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return (
    Instructions()
    .with_callee_name("assert", sensitivity=False)
    .exec(1)
  )
```

## Example Output

<figure><img src="../../.gitbook/assets/image (266).png" alt=""><figcaption></figcaption></figure>
