---
description: Retrieves the address of the external point.
---

# ExternalPoint.get\_address()

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
    print(arguments.list()[0].get_address())
    print(arguments.list()[0].source_code())

    return functions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-16 at 2.33.19 PM.png" alt=""><figcaption></figcaption></figure>
