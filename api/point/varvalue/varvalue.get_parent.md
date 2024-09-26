---
description: Returns parent function/modifier of the variable.
---

# VarValue.get\_parent()

`get_parent() →` [`Callable`](../../callable/)

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1, 2)

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      if isinstance(component, VarValue):
        parent = component.get_parent()
        print(parent)
        
  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

