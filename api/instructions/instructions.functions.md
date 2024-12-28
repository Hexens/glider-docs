---
description: >-
  Returns Functions object for the functions of the instructions. Note: The
  function will return parent functions for those instructions that belong to a
  function, not to a modifier. To get parent modif
---

# Instructions.functions()

**`functions`**`() →` [`Functions`](../callables/functions/)

## Query Example

```python
from glider import *

def query():
  
  return Instructions().functions().exec(1)
```

## Output Example

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
