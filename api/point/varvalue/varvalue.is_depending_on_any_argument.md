---
description: Returns whether the object depends on any of its function's arguments.
---

# VarValue.is\_depending\_on\_any\_argument()

## Query Example

```python
from glider import *


def query():
  instructions = (
    Functions()
    .with_name("insertAccountProfile")
    .exec(1)
    .instructions()
    .exec()
  )

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      if isinstance(component, VarValue):
        depend_on_argument = component.is_depending_on_any_argument()
        if depend_on_argument:
          print(component.expression)
          print(instruction.source_code())
        
  return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 2.38.32 PM.png" alt=""><figcaption></figcaption></figure>
