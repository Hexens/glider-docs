---
description: >-
  Returns all tainted sources that influence the point. This includes not only
  tainted sources within the current function but also extends to sources
  belonging to other functions.
---

# Point.get\_tainted\_sources\_affecting\_point()

`get_tainted_sources_affecting_point() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](./)`]`

Returns A set of tainted sources that affect the point.

## Query Example

```python
from glider import *


def query():

  instructions = Instructions().exec(1,1)

  affected_points = instructions[0].get_tainted_sources_affecting_point()
  print(affected_points)
  for point in affected_points:
    print(point.source_code())
  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>



