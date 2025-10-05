---
description: Returns the i-th argument of called function
---

# Call.get\_arg()

`get_arg(i: int) -> Union[`[`Value`](../value/)`,` [`NoneObject`](../../internal/noneobject/)`]`

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .with_callee_name("require")
        .calls()
        .exec(10)
    )

    for ins in instructions:
        call = ins.get_value()
        if isinstance(call, Call):
            print(call.name)
            print(call.get_arg(0).expression)
            print(call.get_arg(1).expression)

    return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 12.28.13 PM.png" alt=""><figcaption></figcaption></figure>
