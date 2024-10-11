---
description: Returns the value expression's components
---

# ValueExpression.get\_components()

`get_components(self) -> APIList[Union[`[`Value`](../value/)`,` [`NoneObject`](../../internal/noneobject/)`]]`

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(1,27)
    )
    for instruction in instructions:
        for component in instruction.get_value().get_components():
            print(component)
            print(component.expression)
    return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>
