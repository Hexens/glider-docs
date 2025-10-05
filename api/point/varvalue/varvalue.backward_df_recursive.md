---
description: >-
  Returns the list of all previous points of the current point in the current
  data flow graph and outside of that.
---

# VarValue.backward\_df\_recursive()

`backward_df_recursive() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](../point/)`]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1, 187)

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      points = component.backward_df_recursive()
      print(points)
      for backward_df in points:
        print(backward_df.source_code())

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (15) (1) (1).png" alt=""><figcaption></figcaption></figure>

To clarify, what is the difference between `backward_df` and `backward_df_recursive`? `backward_df_recursive` operates recursively. Below is the output when `backward_df` was used instead of `backward_df_recursive` :

<figure><img src="../../../.gitbook/assets/image (16) (1) (1).png" alt=""><figcaption></figcaption></figure>
