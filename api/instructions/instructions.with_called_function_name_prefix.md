---
description: >-
  Adds a filter to get instructions that call a function whose name has the
  given prefix.
---

# Instructions.with\_callee\_function\_name\_prefix()

`with_callee_function_name_prefix(prefix: str, sensitivity: bool = True) →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  return (
    Instructions()
    .with_callee_function_name_prefix("upgrade")
    .exec(1)
  )
```

## Output Example

<figure><img src="../../.gitbook/assets/image (267).png" alt=""><figcaption></figcaption></figure>
