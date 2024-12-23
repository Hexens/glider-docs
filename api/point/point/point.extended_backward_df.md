---
description: >-
  Returns the list of all previous points of the current point in the current
  data flow graph and outside of that.
---

# Point.extended\_backward\_df()

`extended_backward_df() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](./)`]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1,1200)

  res = []
  res.append(instructions[0])
  extended_backward_dfs = instructions[0].extended_backward_df()
  print(f"Count of Points returned by extended_backward_df: {len(extended_backward_dfs)}")
  for extended_backward_df in extended_backward_dfs:
    print(extended_backward_df.source_code())
    res.append(extended_backward_df)
  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (24) (1).png" alt=""><figcaption></figcaption></figure>

To clarify, what is the difference between `backward_df` and `extended_backward_df`? `extended_backward_df` operates recursively. Below is the output when `backward_df` was used instead of `extended_backward_df`

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>
