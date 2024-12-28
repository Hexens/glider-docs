---
description: Returns continue instructions of the function/modifier.
---

# Callable.continue\_instructions()

`continue_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  continue_instructions = []
  for function in functions:
    # List all continue instructions inside the given functions
    for instruction in function.continue_instructions().exec():
      continue_instructions.append(instruction)

  return continue_instructions
```

## Example output

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
