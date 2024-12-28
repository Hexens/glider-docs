---
description: >-
  Adds a filter to get instructions that don't call a function with the given
  name.
---

# Instructions.without\_callee\_function\_name()

`without_callee_function_name(name: str, sensitivity: bool = True) →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  return (
    Instructions()
    .without_callee_function_name("keccka256")
    .exec(2,1)
  )
```

## Output Example

<figure><img src="../../.gitbook/assets/image (273).png" alt=""><figcaption></figcaption></figure>
