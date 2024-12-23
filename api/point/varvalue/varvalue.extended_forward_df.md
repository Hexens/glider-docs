---
description: >-
  Returns the list of all points following the current point in the current data
  flow graph and outside of that.
---

# VarValue.extended\_forward\_df()

`extended_forward_df() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](../point/)`]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1, 611)

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      if isinstance(component, VarValue):
        points = component.extended_forward_df()
        for extended_forward_df in points:
          print(extended_forward_df.source_code())

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (18) (1).png" alt=""><figcaption></figcaption></figure>

To clarify, what is the difference between `forward_df` and `extended_forward_df`? `extended_forward_df` operates recursively. Below is the output when `forward_df` was used instead of `extended_forward_df`

<figure><img src="../../../.gitbook/assets/Screenshot 2024-09-26 at 15.30.52.png" alt=""><figcaption></figcaption></figure>
