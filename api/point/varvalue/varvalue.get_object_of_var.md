---
description: Returns corresponding object of the variable.
---

# VarValue.get\_object\_of\_var()

`get_object_of_var() →` [`LocalVariable`](../../variables/localvariables/localvariable/) `|` [`StateVariable`](../../variables/statevariables/statevariable.md) `|` [`ArgumentVariable`](../../variables/argumentvariables.md) `|` [`GlobalVariable`](../../variables/globalvariables.md) `|` [`NoneObject`](../../internal/noneobject/)

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1, 2)

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      if isinstance(component, VarValue):
        var_object = component.get_object_of_var()
        print(var_object)
        print(var_object.source_code())

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

