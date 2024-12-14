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
        .exec(1, 89)
        .filter(lambda x: x.is_call())
    )

    for ins in instructions:
        call = ins.get_value()
        if isinstance(call, Call):
            print(call.get_arg(0).expression)
            print(call.get_arg(1).expression)
            print(call.get_arg(2).expression)

    return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (2) (1).png" alt=""><figcaption></figcaption></figure>
