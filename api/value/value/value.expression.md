---
description: Returns the value's expression.
---

# Value.expression

`property expression: str`

The property returns the "part" of the instruction that the Value represents.

## Query Example

```python
from glider import *


def query():
    instructions = (
        Instructions()
        .exec(1, 100)
    )
    
    for instruction in instructions:
        print(instruction.get_components().expression)
        
    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-08 at 11.05.44 AM.png" alt=""><figcaption></figcaption></figure>

