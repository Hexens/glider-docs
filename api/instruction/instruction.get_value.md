---
description: Returns the Instruction's Value object.
---

# Instruction.get\_value()

`get_value() ->` [`Value`](../value/) `|` [`NoneObject`](../internal/noneobject/)

## Query Example

```python
from glider import *

def query():
    instructions = Instructions().exec(2,1)
    results = []
    
    for inst in instructions: 
        print(inst.get_value())

    return instructions
```

## Example Output

<figure><img src="../../.gitbook/assets/image (189).png" alt=""><figcaption></figcaption></figure>
