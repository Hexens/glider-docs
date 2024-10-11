---
description: >-
  Returns a list of VarValue objects of current value whose corresponding object
  is a LocalVariable.
---

# Value.get\_local\_vars()

`get_local_vars() ->` [`APIList`](../../iterables/apilist.md)`[`[`VarValue`](../../point/varvalue/)`]`

The function returns all the local variables used (read/written) inside the Value.

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(1,79)
    )
    for instruction in instructions:
        print(instruction.get_components().get_local_vars().expression)
    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2024-10-11 at 15.27.43.png" alt=""><figcaption></figcaption></figure>

