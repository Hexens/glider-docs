---
description: Returns metadata on all calls in the Instruction.
---

# Instruction.get\_callees()

`get_callees() → Dict`

## Query Example

```python
from glider import *

def query():
    instructions = Instructions().exec(3,182)
    results = []
    
    for inst in instructions: 
        print(inst.get_callees())

    return instructions
```

## Example Output

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
