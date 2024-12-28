---
description: >-
  Returns the selector (4 bytes of keccak256 hash) of the function's or
  modifier's signature.
---

# Callable.hashed\_signature()

`hashed_signature() → int`

## Example

```python
from glider import *
def query():
  functions = Functions().exec(3)
  
  for func in functions:
    print({"function": func.name, "sig": func.hashed_signature()})

  return functions
```

## Example output

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
