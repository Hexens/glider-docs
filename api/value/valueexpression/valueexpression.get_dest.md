---
description: >-
  Returns the Value object representing the leftmost destination of the
  instruction
---

# ValueExpression.get\_dest()

`get_dest() -> Union[`[`Value`](../value/)`,` [`NoneObject`](../../internal/noneobject/)`]`

This function will return '`a`' in this case: '`a = b = c = 5`'

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(1,1)
    )
    for instruction in instructions:
        print(instruction.get_value().get_dest().expression)
    return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (3) (1) (2).png" alt=""><figcaption></figcaption></figure>
