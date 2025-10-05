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
        .exec(1, 6)
    )
    for instruction in instructions:
        main_value = instruction.get_value()

        if isinstance(main_value, ValueExpression):
          for component in main_value.get_components():
              print(component)
              print(component.expression)
              
    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-08 at 1.49.30 PM.png" alt=""><figcaption></figcaption></figure>
