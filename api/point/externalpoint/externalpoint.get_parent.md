---
description: Returns parent function/modifier of the ExternalPoint.
---

# ExternalPoint.get\_parent()

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

    print(arguments.with_type("address")[0].get_parent())
    print(arguments.with_type("address")[0].get_variable().source_code())


    return functions
```

## Example Output

<figure><img src="../../../.gitbook/assets/image (275).png" alt=""><figcaption></figcaption></figure>
