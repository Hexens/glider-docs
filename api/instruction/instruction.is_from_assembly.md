---
description: >-
  Returns true if the instruction is from assembly block, otherwise returns
  false.
---

# Instruction.is\_from\_assembly()

`is_from_assembly() -> bool`

## Query Example

```python
from glider import *

def query():
  return Instructions().exec(1000).filter(lambda x: x.is_from_assembly())
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output Example

<figure><img src="../../.gitbook/assets/image (194).png" alt=""><figcaption></figcaption></figure>
