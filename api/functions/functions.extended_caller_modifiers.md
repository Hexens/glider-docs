---
description: >-
  Returns a Modifiers object representing the modifiers through which the
  functions from current Functions object could be called.
---

# Functions.extended\_caller\_modifiers()

`extended_caller_modifiers() →` [`Modifiers`](../callables/modifiers/)

The function will retrieve _**extended**_**/**_**inter-procedural**_ modifiers, meaning it works recursively. It returns the Modifiers object representing all the modifiers that ultimately call the function in question.

## Query Example

```python
from glider import *

def query():
  funcs = Functions().with_name("onlyOwner").extended_caller_modifiers().exec(2)
  
  return funcs
```

## Output Example

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
