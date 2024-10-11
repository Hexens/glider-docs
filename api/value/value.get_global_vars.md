---
description: >-
  Returns a list of VarValue objects of current value whose corresponding object
  is a GlobalVariable.
---

# Value.get\_global\_vars()

`get_global_vars() ->` [`APIList`](../iterables/apilist.md)`[`[`VarValue`](../point/varvalue/)`]`

The function returns all the global variables, e.g. `msg.sender, msg.value, tx.origin, ...`, used inside the Value.

For the list of global variables, please refer to GlobalVariables.

## Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(1,1)
    )
    for instruction in instructions:
        print(instruction.get_components().get_global_vars().expression)
    return instructions
```

## Example Output

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>
