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

Sometimes, the qualifier itself is a call. In that case, you will be returned another Call.

## **Query Example**

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .low_level_external_calls()
        .exec(1000)
        .filter(lambda instruction : instruction.get_parent().get_contract().name == "PoolEth")
    )

    for ins in instructions:
        print(ins.get_value().get_callee_values()[0].get_call_qualifier())
        print(ins.get_value().get_callee_values()[0].get_call_qualifier().expression)

    return instructions
```

## **Example Output**

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 1.04.07 PM.png" alt=""><figcaption></figcaption></figure>
