---
description: Returns start assembly instructions of the function/modifier.
---

# Callable.start\_asm\_instructions()

`start_asm_instructions() →` [`Instructions`](../instructions/)

## Query Example

```python
from glider import *

def query():
  functions = Functions().exec(100)

  start_asm_instructions = []
  for function in functions:
    for instruction in function.start_asm_instructions().exec():
      # Return the start assembly instructions for each function
      start_asm_instructions.append(instruction)

  return start_asm_instructions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

