---
description: >-
  Returns a list of VarValue objects of current value whose corresponding object
  is a StateVariable.
---

# Value.get\_state\_vars()

`get_state_vars() ->`[`APIList`](../../iterables/apilist.md)`[`[`VarValue`](../../point/varvalue/)`]`

The function returns all the state variables used (read/written) inside the Value.

## Example

```python
from glider import *

def query():
    instructions = (
        Functions()
        .with_one_property([MethodProp.HAS_STATE_VARIABLES_READ,MethodProp.HAS_STATE_VARIABLES_WRITTEN])
        .instructions()
        .exec(1,2)
    )
    for instruction in instructions:
        print(instruction.get_components().get_state_vars().expression)
    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>
