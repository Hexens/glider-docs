---
description: Returns start_loop instructions of the function/modifier.
---

# Callable.start\_loop\_instructions()

`start_loop_instructions() →` [`Instructions`](../instructions/)

The functions will return start\_loop instructions for all types of loops e.g. while/for.

start\_loop instruction is not a "real" instruction but rather an abstract one representing the start of the loop.

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  loop_instructions = []
  for function in functions:
    for instruction in function.start_loop_instructions().exec():
      # Return the starting loop instructions for each function
      loop_instructions.append(instruction)

  return loop_instructions
```

## Example output

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
