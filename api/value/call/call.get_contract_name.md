---
description: Returns the name of the contract in which the called function is
---

# Call.get\_contract\_name()

`get_contract_name() -> str`

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
        print(ins.get_value().get_contract_name())

    return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>
