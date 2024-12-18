---
description: Returns end_if instructions of the function/modifier.
---

# Callable.end\_if\_instructions()

`end_if_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  conditional = []
  for function in functions:
    for if_instruction in function.end_if_instructions().exec():
      # For each function, return the conditional (if) instructions
      conditional.append(if_instruction)

  return conditional
```

## Example output

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
