---
description: Returns the points which define the variable.
---

# VarValue.get\_defining\_points()

`get_defining_points() →` [`APIList`](../../iterables/apilist.md)`[`[`Point`](../point/)`]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1, 2)

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      if isinstance(component, VarValue):
        defining_points = component.get_defining_points()
        print(defining_points)
        if len(defining_points):
          print(defining_points[0].source_code())

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

