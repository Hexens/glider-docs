---
description: >-
  Returns the arguments of the call, or empty array if the call has no
  arguments.
---

# Call.get\_args()

`get_args() ->` [`APIList`](../../iterables/apilist.md)`[Union[`[`Value`](../value/)`,` [`NoneObject`](../../internal/noneobject/)`]]`

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(100)
        .filter(lambda x: x.is_call())
    )

    for ins in instructions:
        call = ins.get_value()
        if isinstance(call, Call):
            print(call.get_args().expression)

    return instructions
```

## Output&#x20;

<figure><img src="../../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>
