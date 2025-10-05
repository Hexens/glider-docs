---
description: Convert ArgumentPoints to List[ArgumentPoint]
---

# ArgumentPoints.list()

`list() ->` [`APIList`](../../iterables/apilist.md)`[`[`ArgumentPoint`](../argumentpoint.md)`]`

## Query Example

```python
from glider import *


def query():
    functions = (
        Functions()
        .with_name("transferFrom")
        .exec(1)
    )

    arguments = functions[0].arguments()
    print(f"Arguments: {arguments}")
    print(f"List of arguments: {arguments.list()}")

    return functions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>
