---
description: Return object of argument variable
---

# ArgumentPoint.get\_variable()

`get_variable() →` [`ArgumentVariable`](../../variables/argumentvariables.md)

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

    print(arguments.with_type("address")[0].get_variable())
    print(arguments.with_type("address")[0].get_variable().source_code())


    return functions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (13) (1) (1).png" alt=""><figcaption></figcaption></figure>
