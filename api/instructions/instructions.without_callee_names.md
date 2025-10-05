---
description: >-
  Adds a filter to get instructions that don't call a function with the given
  name.
---

# Instructions.without\_callee\_names()

`without_callee_names(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return (
    Instructions()
    .without_callee_names(["transfer", "transferFrom"])
    .exec(3, 101)
  )
```

## Example Output

<figure><img src="../../.gitbook/assets/image (274).png" alt=""><figcaption></figcaption></figure>
