---
description: Returns the list of ArgumentPoints having specified memory type.
---

# ArgumentsPoints.with\_memory\_type()

`with_memory_type(memory_type: str) →` [`APIList`](../../iterables/apilist.md)`[`[`ArgumentPoint`](../argumentpoint.md)`]`



## Query Example

```python
from glider import *

def query():
    functions = (
        Functions()
        .with_name("observe")
        .exec(1)
    )

    arguments = functions[0].arguments()

    print(arguments.with_memory_type("calldata").source_code())

    return functions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>



