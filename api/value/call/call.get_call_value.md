---
description: >-
  Returns the Value representing the "value" (ether sent) during the external
  call
---

# Call.get\_call\_value()

`get_call_value() → List[`[`Value`](../)`]`

As some types of calls can have, a special parameter set representing the ether value to send in the call), this function can be used to retrieve that value.

For example, in the call:

```solidity
(bool success, ) = recipient.call{value: amount}("");
```

The special parameter `value` is being set: `{value: amount}`

and the function will return the Value representing the:

`amount`

**Query Example**

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .low_level_function_calls()
        .exec(1)
    )

    for ins in instructions:
        print(ins.get_value().get_callee_values()[0].get_call_value())
        print(ins.get_value().get_callee_values()[0].get_call_value().expression)


    return instructions
```

**Output Example**

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
