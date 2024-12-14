---
description: Returns the call's qualifier (target) is exists
---

# Call.get\_call\_qualifier()

`get_call_qualifier() -> Union[`[`Value`](../value/)`,` [`NoneObject`](../../internal/noneobject/)`]`

The call's qualifier is the "target" of the call.

For example, for the call:

```solidity
(bool success_, ) = feeCollector_.call{ value: feeAmount_, gas: 1000 }("");
```

The qualifier is the:

```solidity
feeCollector_
```

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
        print(ins.get_value().get_callee_values()[0].get_call_qualifier())
        print(ins.get_value().get_callee_values()[0].get_call_qualifier().expression)

    return instructions
```

**Output**

<figure><img src="../../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Sometimes, the qualifier itself is a cal
