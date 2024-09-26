---
description: >-
  Returns the first encountered path containing tainted data that influence the
  point, if it exists. Otherwise, returns an empty tuple.
---

# Point.get\_tainted\_path\_affecting\_point()

Returns a path containing tainted data that affect the point.

`get_tainted_path_affecting_point() →` [`APITuple`](../../iterables/apituple.md)`[`[`Point`](./)`]`

## Note

This path can include points belonging to other functions.

## Query Example

```python
from glider import *


def query():

  instructions = Instructions().exec(1,1)

  affected_points = instructions[0].get_tainted_path_affecting_point()
  print(affected_points)
  for point in affected_points:
    print(point.source_code())
  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
