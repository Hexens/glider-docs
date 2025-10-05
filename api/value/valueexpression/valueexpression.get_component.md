---
description: Returns the value expression's i-th component
---

# ValueExpression.get\_component()

`get_component(i: int) -> Union[`[`Value`](../value/)`,` [`NoneObject`](../../internal/noneobject/)`]`

## Query Example

```python
from glider import *


def query():
    instructions = (
        Instructions()
        .new_variable_instructions()
        .exec(1,1)
    )
    for instruction in instructions:
        print(instruction.get_value().get_component(0))
        print(instruction.get_value().get_component(0).expression)
    return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>
