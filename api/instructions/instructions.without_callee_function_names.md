---
description: >-
  Adds a filter to get instructions that don't call a function with the given
  name.
---

# Instructions.without\_callee\_function\_names()

`without_callee_function_names(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  return (
    Instructions()
    .without_callee_function_names(["transfer", "transferFrom"])
    .exec(3, 101)
  )
```

## Output Example

<figure><img src="../../.gitbook/assets/image (274).png" alt=""><figcaption></figcaption></figure>
