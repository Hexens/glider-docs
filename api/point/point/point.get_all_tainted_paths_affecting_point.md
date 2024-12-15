---
description: >-
  Returns all paths containing tainted data that influence the point. This
  includes not only tainted paths within the current function but also extends
  to paths belonging to other functions.
---

# Point.get\_all\_tainted\_paths\_affecting\_point()

`get_all_tainted_paths_affecting_point() →` [`APISet`](../../iterables/apiset.md)`[`[`APITuple`](../../iterables/apituple.md)`[`[`Point`](./)`]]`

Returns a set of paths containing tainted data that affect the point.

## Query Example

```python
from glider import *


def query():

  instructions = Instructions().exec(1,1)

  affected_points = instructions[0].get_all_tainted_paths_affecting_point()
  print(affected_points)
  for point in affected_points:
    print(point.source_code())
  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

