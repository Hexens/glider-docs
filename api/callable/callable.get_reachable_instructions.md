---
description: Returns the instructions which are reachable from the entry node
---

# Callable.get\_reachable\_instructions()

`get_reachable_instructions() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](../instruction/)`]`

## Query Example

```python
from glider import *

def query():
    functions = Functions().exec(1) 
  
    for reachable_instruction in functions[0].get_reachable_instructions():
        print(f"{reachable_instruction.source_code()}")

    return functions
```

## Example Output

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
