---
description: Returns the list of ArgumentPoints having specified name.
---

# ArgumentPoints.with\_name()

`with_name(arg_name: str, sensitivity: bool = False) →` [`APIList`](../../iterables/apilist.md)`[`[`ArgumentPoint`](../argumentpoint.md)`]`

## Query Example

```python
from glider import *

def query():
    functions = (
        Functions()
        .with_name("transfer")
        .exec(1)
    )

    arguments = functions[0].arguments()

    print(arguments.with_name("_amount").source_code())

    return functions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (11) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

