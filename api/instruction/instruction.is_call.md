---
description: Returns True if the instruction is call instruction, otherwise returns False.
---

# Instruction.is\_call()

`is_call` -> `bool`

## Query example

```python
from glider import *

def query():
  return Instructions().exec(100).filter(lambda x: x.is_call())
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output example

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
