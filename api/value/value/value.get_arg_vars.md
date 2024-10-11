---
description: >-
  Returns a list of VarValue objects of current value whose corresponding object
  is an argument variable.
---

# Value.get\_arg\_vars()

`get_arg_vars() ->` [`APIList`](../../iterables/apilist.md)`[`[`VarValue`](../../point/varvalue/)`]`

The function returns all the arguments' vars used inside the Value.

## Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(1,10)
    )
    for instruction in instructions:
        print(instruction.get_components().get_arg_vars().expression)
    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
