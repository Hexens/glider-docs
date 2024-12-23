---
description: Returns the list of ArgumentPoints having specified type.
---

# ArgumentPoints.with\_type()

`with_type(arg_type: str) →` [`APIList`](../../iterables/apilist.md)`[`[`ArgumentPoint`](../argumentpoint.md)`]`

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

    print(arguments.with_type("address").source_code())

    return functions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>

