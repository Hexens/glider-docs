---
description: Returns catch instructions of the function/modifier.
---

# Callable.catch\_instructions()

`catch_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(400)

  catch_instructions = []
  for function in functions:
    # List all catch instructions inside a try/catch block from the given functions
    for instruction in function.catch_instructions().exec():
      catch_instructions.append(instruction)

  return catch_instructions
```

## Example output

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
