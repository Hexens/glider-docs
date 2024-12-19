---
description: >-
  Returns an Instructions object for the call instructions of the
  function/modifier.
---

# Callable.calls\_instructions()

`calls_instructions() →` [`Instructions`](../instructions/)

The function returns [Instructions](../instructions/) object for all instructions that have any type of call inside it, whether it is an external, internal, library or other type of call.

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  calls_instructions = []
  for function in functions:
    # List all call instructions in the given functions
    for instruction in function.calls_instructions().exec():
      calls_instructions.append(instruction)

  return calls_instructions
```

## Example output

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
