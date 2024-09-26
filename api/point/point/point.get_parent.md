---
description: Abstract method that returns parent function/modifier of the Point.
---

# Point.get\_parent()

`get_parent() →` [`Callable`](../../callable/) `|` [`NoneObject`](../../internal/noneobject/)

## Query Example

```python
from glider import *


def query():

  instructions = Instructions().exec(1)

  parent = instructions[0].get_parent()

  print(instructions[0].source_code())

  return [parent]
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

