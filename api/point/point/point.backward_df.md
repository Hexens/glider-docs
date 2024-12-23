---
description: >-
  Returns the list of all previous points of the current point in the data flow
  graph.
---

# Point.backward\_df()

`backward_df() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](./)`]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().exec(1,2)

  backward_dfs = instructions[0].backward_df()
  for backward_df in backward_dfs:
    print(backward_df.source_code())

  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (23) (1).png" alt=""><figcaption></figcaption></figure>

