---
description: Returns end_loop instructions of the function/modifier.
---

# Callable.end\_loop\_instructions()

`end_loop_instructions() →` [`Instructions`](../instructions/)

The functions will return end\_loop instructions for all types of loops e.g. while/for

end\_loop instruction is not a "real" instruction but rather an abstract one representing the end of the loop.

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  loop = []
  for function in functions:
    for loop_instruction in function.end_loop_instructions().exec():
      # For each function, return the loop instructions
      loop.append(loop_instruction)

  return loop
```

## Example output

<figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
