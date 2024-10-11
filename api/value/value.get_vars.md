---
description: Returns a list of all VarValue objects of current value.
---

# Value.get\_vars()

`get_vars() ->` [`APIList`](../iterables/apilist.md)`[`[`VarValue`](../point/varvalue/)`]`

The function returns all the VarValues used (read/written) inside the Value.&#x20;

It returns VarValues for state, local and global variables and arguments, basically combining the calls to get\_state\_vars, get\_local\_vars, get\_global\_vars and get\_arg\_vars.

## Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(1,10)
    )
    for instruction in instructions:
        print(instruction.get_components().get_vars().expression)
    return instructions
```

## Example Output

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>
