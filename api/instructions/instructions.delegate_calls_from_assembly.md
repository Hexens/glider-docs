---
description: Returns a list of delegate call instructions from assembly.
---

# Instructions.delegate\_calls\_from\_assembly()

`delegate_calls_from_assembly() →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return Instructions().delegate_calls_from_assembly().exec(1)
```

## Example Output

<figure><img src="../../.gitbook/assets/image (245).png" alt=""><figcaption></figcaption></figure>
