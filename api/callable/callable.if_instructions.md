---
description: Returns if instructions of the function/modifier.
---

# Callable.if\_instructions()

`if_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(50)

  if_instructions = []
  for function in functions:
    for instruction in function.if_instructions().exec():
      if_instructions.append(instruction)

  return if_instructions
```

## Example output

<figure><img src="../../.gitbook/assets/image (131).png" alt=""><figcaption></figcaption></figure>
