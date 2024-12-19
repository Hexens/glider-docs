---
description: Returns if_loop instructions of the function/modifier.
---

# Callable.if\_loop\_instructions()

`if_loop_instructions() →` [`Instructions`](../instructions/)

The function returns [Instructions](../instructions/) that represent the condition part in loop operators. It will return for all types of loops e.g. while and for

## Example

```python
from glider import *
def query():
  functions = Functions().without_modifier_names(["onlyOwner"]).exec(100)

  if_loop_instructions = []
  for function in functions:
    # For each function without an "onlyOwner" modifier, return the if loop instructions
    for instruction in function.if_loop_instructions().exec():
      if_loop_instructions.append(instruction)

  return if_loop_instructions
```

## Example output

<figure><img src="../../.gitbook/assets/image (132).png" alt=""><figcaption></figcaption></figure>
