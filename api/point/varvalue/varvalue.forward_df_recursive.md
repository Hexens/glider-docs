---
description: >-
  Returns the list of all points following the current point in the current data
  flow graph and outside of that.
---

# VarValue.forward\_df\_recursive()

`forward_df_recursive() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](../point/)`]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1, 611)

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      if isinstance(component, VarValue):
        points = component.forward_df_recursive()
        for forward_df in points:
          print(forward_df.source_code())

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (18) (1).png" alt=""><figcaption></figcaption></figure>

To clarify, what is the difference between `forward_df` and `forward_df_recursive`? `forward_df_recursive` operates recursively. Below is the output when `forward_df` was used instead of `forward_df_recursive` :

<figure><img src="../../../.gitbook/assets/Screenshot 2024-09-26 at 15.30.52.png" alt=""><figcaption></figcaption></figure>
