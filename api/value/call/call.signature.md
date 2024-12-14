---
description: Returns the called function signature
---

# Call.signature

`property | signature() -> str`

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
        print(ins.get_value().signature)

    return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (2) (1) (2).png" alt=""><figcaption></figcaption></figure>
