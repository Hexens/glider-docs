---
description: Returns the type of the literal.
---

# Literal.type

## Query Example

```python
from glider import *


def query():
    functions = (
        Functions()
        .with_name("mul")
        .exec(1)
    )
    instructions = functions[0].instructions().exec()
    for instruction in instructions:
        for component in instruction.get_components():
            if isinstance(component, Literal):                  
                print(component.type)
                print(component.expression)

              
    return [instructions[0]]
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 12.16.56 PM.png" alt=""><figcaption></figcaption></figure>

