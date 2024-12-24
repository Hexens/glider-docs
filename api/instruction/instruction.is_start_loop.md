---
description: >-
  Returns true if the instruction is start_loop instruction, otherwise returns
  false.
---

# Instruction.is\_start\_loop()

`is_start_loop()` -> `bool`

## Output Example

```python
from glider import *

def query():
  return Instructions().exec(1000).filter(lambda x: x.is_start_loop())
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Query Example

<figure><img src="../../.gitbook/assets/image (202).png" alt=""><figcaption></figcaption></figure>
