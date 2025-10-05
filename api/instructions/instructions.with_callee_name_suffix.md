---
description: >-
  Adds a filter to get instructions that call a function whose name has the
  given suffix.
---

# Instructions.with\_callee\_name\_suffix()

`with_callee_name_suffix(suffix: str, sensitivity: bool = True) →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return (
    Instructions()
    .with_callee_name_suffix("dao", sensitivity=False)
    .exec(2,10)
  )
```

## Example Output

<figure><img src="../../.gitbook/assets/image (268).png" alt=""><figcaption></figcaption></figure>
