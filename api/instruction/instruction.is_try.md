---
description: >-
  Returns True if the instruction is Try instruction in a try-catch block,
  otherwise returns False.
---

# Instruction.is\_try()

`is_try()` -> `bool`

## Query Example

```python
from glider import *

def query():
  return Instructions().exec(2000).filter(lambda x: x.is_try())
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output Example

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
