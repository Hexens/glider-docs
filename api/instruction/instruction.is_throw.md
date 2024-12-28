---
description: Returns True if the instruction is throw instruction, otherwise returns False.
---

# Instruction.is\_throw()

`is_throw()` -> `bool`

## Query Example

```python
from glider import *

def query():
  return Instructions().exec(30).filter(lambda x: x.is_throw())
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output Example

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
