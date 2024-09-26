---
description: >-
  Returns the list of all points following the current point in the current data
  flow graph.
---

# VarValue.forward\_df()

`forward_df() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](../point/)`]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1, 611)

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      if isinstance(component, VarValue):
        points = component.forward_df()
        print(points)
        for forward_df in points:
          print(forward_df.source_code())

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
