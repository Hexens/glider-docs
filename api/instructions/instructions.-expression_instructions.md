---
description: Returns an Instructions object for the 'expression' instructions.
---

# Instructions.expression\_instructions()

`expression_instructions() →` [`Instructions`](./)

In Glider, all objects lacking defined types, such as [`IfInstruction`](../instruction/ifinstruction/), [`CatchInstruction`](../instruction/catchinstruction/), [`BreakInstruction`](../instruction/breakinstruction.md), etc., are considered `expressions`

## Query Example

```python
from glider import *

def query():
  
  return Instructions().expression_instructions().exec(4)
```

## Output Example

<figure><img src="../../.gitbook/assets/image (252).png" alt=""><figcaption></figcaption></figure>
