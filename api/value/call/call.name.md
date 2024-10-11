---
description: Returns the called function name
---

# Call.name

`property | name() -> str`

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(1,98)
        .filter(lambda x: x.is_call())
    )

    for ins in instructions:
        print(ins.get_value().name)

    return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
