---
description: Returns the instruction's i-th component.
---

# Instruction.get\_component()

`get_component(`_`i : int`_`) →` [`Value`](../value/) `|` [`NoneObject`](../internal/noneobject/)

## Query Example

```python
from glider import *

def query():
    instructions = Instructions().exec(1,1)
  
    print(instructions[0].get_component(0).expression)
    return instructions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>
