---
description: >-
  Returns True if the instruction is a storage read instruction, else returns
  False. A storage read instruction just reads the value of a state variable
  without making any changes to it
---

# Instruction.is\_storage\_read()

`is_storage_write()` -> `bool`

## Query Example

```python
from glider import *

def query():
  return Instructions().exec(10).filter(lambda x: x.is_storage_read())
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output Example

<figure><img src="../../.gitbook/assets/image (203).png" alt=""><figcaption></figcaption></figure>
