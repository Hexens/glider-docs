---
description: Returns a list of all library call instructions.
---

# Instructions.library\_calls()

**`library_calls`**`() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():

  return Instructions().library_calls().exec(1,4)
```

## Output Example

<figure><img src="../../.gitbook/assets/image (255).png" alt=""><figcaption></figcaption></figure>

This outputs the call to the `Math.log10(value)` library function.
