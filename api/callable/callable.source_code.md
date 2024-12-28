---
description: Returns the source code of the function/modifier.
---

# Callable.source\_code()

`source_code() → str`

## Example

```python
from glider import *
def query():
  functions = Functions().exec(1,1)

  for function in functions:
    # Aggregate the code of each function along with their name
    print(f"function: {function.name}, code: {function.source_code()}")

  return functions
```

## Example output

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
