---
description: >-
  Returns true if the instruction is  an expression instruction, otherwise
  returns false.
---

# Instruction.is\_expression()

`is_expression()` -> `bool`

## Query Example

```python
from glider import *

def query():
  return Instructions().exec(1000).filter(lambda x: x.is_expression())
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output Example

<figure><img src="../../.gitbook/assets/image (193).png" alt=""><figcaption></figcaption></figure>
