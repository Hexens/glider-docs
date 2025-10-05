---
description: >-
  Returns a Modifiers object representing the modifiers through which the
  functions from current Functions object could be called.
---

# Functions.caller\_modifiers\_recursive()

`caller_modifiers_recursive() →` [`Modifiers`](../callables/modifiers/)

The function will retrieve _**extended**_**/**_**inter-procedural**_ modifiers, meaning it works recursively. It returns the Modifiers object representing all the modifiers that ultimately call the function in question.

## Query Example

```python
from glider import *

def query():
  modifiers = Functions().with_name("onlyOwner").caller_modifiers_recursive().exec(2)
  
  return modifiers
```

## Example Output

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
