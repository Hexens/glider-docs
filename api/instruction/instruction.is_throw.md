---
description: Returns True if the instruction is throw instruction, otherwise returns False.
---

# Instruction.is\_throw()

`is_throw()` -> `bool`

## Query Example

```python
from glider import *


def query():
  return (
    Functions()
    .with_name("BliBliToken")
    .exec(1)
    .instructions()
    .exec()
    .filter(lambda x: x.is_throw())
  ) 
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-03 at 12.59.15 PM.png" alt=""><figcaption></figcaption></figure>
