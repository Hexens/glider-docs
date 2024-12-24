---
description: Returns throw instructions of the function/modifier.
---

# Callable.throw\_instructions()

`throw_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(10000)

  throw_instructions = []
  for function in functions:
    for instruction in function.throw_instructions().exec():
      # Return the throw instructions for each function
      throw_instructions.append(instruction)

  return throw_instructions
```

## Example output



<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
