---
description: Returns the type of the call
---

# Call.get\_call\_type()

`get_call_type() →` [`CallType`](calltype/)

The Call represents all types of call values: external, internal, log emit, etc. This function can be used to get the type of the call.

**Query Example**

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
            print(call.get_call_type())

    return instructions
```

**Output**

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
