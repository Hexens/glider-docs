---
description: Returns end_assembly instructions of the function/modifier.
---

# Callable.end\_asm\_instructions()

`end_asm_instructions() →` [`Instructions`](../instructions/)

## Query Example

```python
from glider import *

def query():
    functions = Functions().exec(100)

    assembly = []
    for function in functions:
        for asm_instruction in function.end_asm_instructions().exec():
            # For each function, return the assembly instructions
            assembly.append(asm_instruction)

    return assembly
```

## Example Output

<figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>
