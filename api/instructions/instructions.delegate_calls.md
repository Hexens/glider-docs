---
description: Returns a list of all delegate call instructions.
---

# Instructions.delegate\_calls()

`delegate_calls() →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return Instructions().delegate_calls().exec(1)
```

## Example Output

<figure><img src="../../.gitbook/assets/image (244).png" alt=""><figcaption></figcaption></figure>
