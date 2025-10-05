---
description: >-
  Returns True if the instruction is CONTINUE instruction, otherwise returns
  False.
---

# Instruction.is\_continue()

`is_continue()` -> `bool`

## Query Example

```python
from glider import *

def query():
  return Instructions().exec(100000).filter(lambda x: x.is_continue())
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output Example

<figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
