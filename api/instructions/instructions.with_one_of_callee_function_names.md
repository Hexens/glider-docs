---
description: >-
  Adds a filter to get Instructions that call a function with the given
  signature.
---

# Instructions.with\_one\_of\_callee\_function\_names()

`with_one_of_callee_function_names(names: List[str], sensitivity: bool = True) →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  return (
    Instructions()
    .with_one_of_callee_function_names(["deposit", "withdraw"])
    .exec(2,1)
  )
```

## Output Example

<figure><img src="../../.gitbook/assets/image (271).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (272).png" alt=""><figcaption></figcaption></figure>
