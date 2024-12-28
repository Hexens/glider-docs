---
description: Returns entry_point instructions of the function/modifier.
---

# Callable.entry\_point\_instructions()

`entry_point_instructions() →` [`Instructions`](../instructions/)

The entry\_point of a function is not a "real" instruction, but rather an abstract instruction representing the starting point of the function.

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  entry_points = []
  for function in functions:
    for entry_point_instruction in function.entry_point_instructions().exec():
      # For each function, return entry points
      entry_points.append(entry_point_instruction)

  return entry_points
```

## Example output

<figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
