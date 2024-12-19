---
description: Returns try instructions of the function/modifier.
---

# Callable.try\_instructions()

`try_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(1000)

  try_instructions = []
  for function in functions:
    for instruction in function.try_instructions().exec():
      # Return the try instructions for each function
      try_instructions.append(instruction)

  return try_instructions
```

## Example output

<figure><img src="../../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>
