---
description: Returns true if the instruction creates a new contract.
---

# Instruction.is\_new\_contract()

`is_new_contract() -> bool`

## Query Example

```python
from glider import *

def query():
  ins = (
    Functions()
    .with_name("deploy")
    .instructions()
    .exec(100)
    .filter(lambda x: x.is_new_contract())
  )
  return ins
```

With the Glider 1.0 update, calling the [`exec`](../instructions/instructions.exec.md) function returns an [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`. You can then use [`Instruction`](./) functions, which are applied to each element of the [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Output Example

<figure><img src="../../.gitbook/assets/image (198).png" alt=""><figcaption></figcaption></figure>
