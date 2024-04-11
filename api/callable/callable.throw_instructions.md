---
description: Returns throw instructions of the function/modifier.
---

# Callable.throw\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  throw_instructions = []
  for function in functions:
    for instruction in function.throw_instructions().exec():
      # Return the throw instructions for each function
      throw_instructions.append(instruction)

  return throw_instructions
```

## Example output

NO\_OUTPUT/MEMORY\_LIMIT
