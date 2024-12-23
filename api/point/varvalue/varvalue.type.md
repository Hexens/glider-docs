---
description: Returns the variable's type.
---

# VarValue.type

property type: Type

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1, 2)

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      if isinstance(component, VarValue):
        var_value_type = component.type 
        print(var_value_type)

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (21) (1).png" alt=""><figcaption></figcaption></figure>
