---
description: >-
  Adds a filter to get instructions that don't call a function with the given
  name.
---

# Instructions.without\_callee\_name()

`without_callee_name(name: str, sensitivity: bool = True) →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return (
    Instructions()
    .without_callee_name("keccak256")
    .exec(2,1)
  )
```

## Example Output

<figure><img src="../../.gitbook/assets/image (273).png" alt=""><figcaption></figcaption></figure>
