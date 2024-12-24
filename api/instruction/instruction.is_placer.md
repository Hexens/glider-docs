---
description: >-
  Returns true if the instruction is placeholder instruction, otherwise returns
  false. A placeholder instruction is generally found in modifiers
---

# Instruction.is\_placer()

`is_placer()` -> `bool`

## Query Example

```python
from glider import *

def query():
  ins = (
    Modifiers()
    .exec(1)
    .instructions()
    .exec()
    .filter(lambda x: x.is_placer())
  )
  return ins
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output Example

<figure><img src="../../.gitbook/assets/image (199).png" alt=""><figcaption></figcaption></figure>
