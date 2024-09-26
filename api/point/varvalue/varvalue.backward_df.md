---
description: >-
  Returns the list of all previous points of the current point in the data flow
  graph.
---

# VarValue.backward\_df()

`backward_df() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](../point/)`]`

## Query Example

```python
from glider import *


def query():
  instrucitons = (
    Instructions()
    .exec(1,30)
  )

  for instruciton in instrucitons:
    components = instruciton.get_components()
    for component in components:
      for backward_df in component.backward_df():
        print(backward_df.source_code())

  return instrucitons
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

