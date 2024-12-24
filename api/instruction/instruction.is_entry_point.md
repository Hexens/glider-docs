---
description: >-
  Returns true if the instruction is entry_point instruction, otherwise returns
  false.
---

# Instruction.is\_entry\_point()

`is_entry_point()` -> `bool`

## Query Example

```python
from glider import *

def query():
  return Instructions().exec(1000).filter(lambda x: x.is_entry_point())
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output Example

<figure><img src="../../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure>
