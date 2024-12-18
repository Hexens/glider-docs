---
description: >-
  Returns a Functions object representing the functions through which the
  functions from current Functions object could be called.
---

# Functions.extended\_caller\_functions()

`extended_caller_functions() →` [`Functions`](../callables/functions/)

The function will retrieve _**extended**_**/**_**inter-procedural**_ functions, meaning it works recursively. It returns the Functions object representing all the functions that ultimately call the function in question.

## Query Example

```python
from glider import *

def query():
  funcs = Functions().with_name("withdrawFromPair").extended_caller_functions().exec(2)
  
  return funcs
```

## Output Example

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
