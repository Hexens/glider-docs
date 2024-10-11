---
description: Returns the list of Call values of current value
---

# Value.get\_callee\_values()

`get_callee_values() ->` [`APIList`](../../iterables/apilist.md)`[`[`Call`](../call/)`]`

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .low_level_function_calls()
        .exec(1, 137)
    )

    for ins in instructions:
        print(ins.get_value().get_callee_values())
        print(ins.get_value().get_callee_values()[0].expression)

    return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>
