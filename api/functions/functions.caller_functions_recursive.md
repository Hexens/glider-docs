---
description: >-
  Returns a Functions object representing the functions through which the
  functions from current Functions object could be called.
---

# Functions.caller\_functions\_recursive()

`caller_functions_recursive() →` [`Functions`](../callables/functions/)

The function will retrieve _**extended**_**/**_**inter-procedural**_ functions, meaning it works recursively. It returns the Functions object representing all the functions that ultimately call the function in question.

## Query Example

```python
from glider import *


def query():
  funcs = Functions().with_name("transfer").caller_functions_recursive().exec(2)
  
  return funcs
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-21 at 9.54.44 AM.png" alt=""><figcaption></figcaption></figure>
