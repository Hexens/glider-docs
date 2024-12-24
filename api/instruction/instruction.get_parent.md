---
description: Returns parent function/modifier of the instruction.
---

# Instruction.get\_parent()

`get_parent() → Callable | NoneObject`

The function returns a [Callable](../callable/) object, specifically either a [Function](../callable/function/) or [Modifier](../callable/modifier/) object, where the current instruction is placed.

## Query Example

```python
from glider import *
def query():
  #return the parent function/modifier of an instruction
  return [Instructions().exec(1)[0].get_parent()]
```

## Output

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
