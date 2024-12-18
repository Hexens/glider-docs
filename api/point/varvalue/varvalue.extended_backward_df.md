---
description: >-
  Returns the list of all previous points of the current point in the current
  data flow graph and outside of that.
---

# VarValue.extended\_backward\_df()

`extended_backward_df() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](../point/)`]`



## Query Example

```python
from glider import *


def query():

  instructions = Instructions().exec(1, 187)

  for instruction in instructions:
    components = instruction.get_components()
    for component in components:
      points = component.extended_backward_df()
      print(points)
      for extended_backward_df in points:
        print(extended_backward_df.source_code())

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>

To clarify, what is the difference between `backward_df` and `extended_backward_df`? `extended_backward_df` operates recursively. Below is the output when `backward_df` was used instead of `extended_backward_df`

<figure><img src="../../../.gitbook/assets/image (16) (1).png" alt=""><figcaption></figcaption></figure>
