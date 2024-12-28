---
description: The method returns a list of instruction in a try block.
---

# TryInstruction.get\_block\_instructions()

`get_block_instructions() -> APIList[`[`Instruction`](../)`]`

## Query Example

```python
from glider import *

def query():
    try_instructions = Instructions().try_instructions().exec(1)

    return try_instructions + try_instructions[0].get_block_instructions()
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (229).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (230).png" alt=""><figcaption></figcaption></figure>
