---
description: Returns the Functions object for the functions of the contracts.
---

# Contracts.functions()

`functions() →` [`Functions`](../callable/function/)

## Example Query

```python
from glider import *

def query():

  functions = Contracts().functions().exec(1)

  return functions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>
