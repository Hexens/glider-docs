---
description: Returns the instruction's components.
---

# Instruction.get\_components()

`get_components() →` [`APIList`](../iterables/apilist.md)`[`[`Value`](../value/) `|` [`NoneObject`](../internal/noneobject/)`]`

## Query Example

```python
from glider import *

def query():
    instructions = Instructions().exec(1,10)
    for inst in instructions:
        for component in inst.get_components():
            print(component.expression)

    return instructions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>
