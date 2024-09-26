---
description: >-
  Returns the list of all points following the current point in the current data
  flow graph and outside of that.
---

# Point.extended\_forward\_df()

`extended_forward_df() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](./)`]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1,1400)

  res = []
  res.append(instructions[0])

  extended_forward_dfs = instructions[0].extended_forward_df()
  print(f"Count of Points returned by forward_df: {len(extended_forward_dfs)}")
  for extended_forward_df in extended_forward_dfs:
    print(extended_forward_df.source_code())
    res.append(extended_forward_df)

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

To clarify, what is the difference between `forward_df` and `extended_forward_df`? `extended_forward_df` operates recursively. Below is the output when `forward_df` was used instead of `extended_forward_df`

<figure><img src="../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>
