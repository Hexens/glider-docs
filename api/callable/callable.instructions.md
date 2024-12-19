---
description: Returns an Instructions object for the instructions of the function/modifier.
---

# Callable.instructions()

`instructions() →` [`Instructions`](../instructions/)

The function will return all of the instructions directly reachable from the function.

## Example

```python
from glider import *
def query():
  functions = Functions().exec(1)

  instructions = []
  for instruction in functions[0].instructions().exec():
    # Return an array of all instructions for a function
    instructions.append(instruction)

  return instructions
```

## Example output

<figure><img src="../../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>
