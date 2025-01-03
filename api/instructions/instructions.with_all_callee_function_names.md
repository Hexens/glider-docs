---
description: Adds a filter to get Instructions that have callees with all the given names.
---

# Instructions.with\_all\_callee\_function\_names()

`with_all_callee_function_names(names: List[str], sensitivity: bool = True) →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  return (
    Instructions()
    .with_all_callee_function_names(["require", "balanceOf"], sensitivity=False)
    .exec(1)
  )
```

## Output Example

<figure><img src="../../.gitbook/assets/image (265).png" alt=""><figcaption></figcaption></figure>
