---
description: Returns Value representing the gas-parameter used in the external calls.
---

# Call.get\_call\_gas()

`get_call_gas() ->` [`APIList`](../../iterables/apilist.md)`[Union[`[`Value`](../value/)`,` [`NoneObject`](../../internal/noneobject/)`]]`

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
        callee_values = ins.get_value().get_callee_values()
        print(callee_values.get_call_gas())
        print(callee_values.get_call_gas().expression)

    return instructions
```

## **Example Output**

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 1.01.24 PM.png" alt=""><figcaption></figcaption></figure>
