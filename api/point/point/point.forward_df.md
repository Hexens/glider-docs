---
description: >-
  Returns the list of all points following the current point in the current data
  flow graph.
---

# Point.forward\_df()

`forward_df() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](./)`]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1,1)

  forward_dfs = instructions[0].forward_df()
  for forward_df in forward_dfs:
    print(forward_df.source_code())

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (22) (1).png" alt=""><figcaption></figcaption></figure>
