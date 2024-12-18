---
description: Abstract method that returns object of variable
---

# ExternalPoint.get\_variable()

`get_variable() →` [`Variable`](../../variables/variable/)

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
    print(arguments.list()[0].get_variable())
    print(arguments.list()[0].source_code())

    return functions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

