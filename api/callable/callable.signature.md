---
description: Returns the function's or modifier's signature.
---

# Callable.signature()

`signature() → str`

## Example

```python
from glider import *
def query():
  functions = Functions().exec(3,3)

  for function in functions:
    # Aggregate the signature of each function along with their name
    print(f"function name {function.name} | signature {function.signature()}")

  return functions
```

## Example output

<figure><img src="../../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>
