---
description: Returns Value representing the gas-parameter used in the external calls.
---

# Call.get\_call\_gas()

`get_call_gas() ->` [`APIList`](../../iterables/apilist.md)`[Union[`[`Value`](../value/)`,` [`NoneObject`](../../internal/noneobject/)`]]`



**Query Example**

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .low_level_function_calls()
        .exec(1, 137)
    )

    for ins in instructions:
        print(ins.get_value().get_callee_values().get_call_gas())
        print(ins.get_value().get_callee_values().get_call_gas().expression)

    return instructions
```

**Output**

<figure><img src="../../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>
