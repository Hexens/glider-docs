---
description: Returns all instructions from the catch block
---

# CatchInstruction.get\_block\_instructions()

`get_block_instructions() ->` [`APIList`](../../iterables/apilist.md)`[`[`Instruction`](../)`]`

## Query Example

```python
from glider import *

def query():
    catch_instructions = Instructions().catch_instructions().exec(1,1)

    return catch_instructions + catch_instructions[0].get_block_instructions()
```

## Example Output

<figure><img src="../../../.gitbook/assets/image (232).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (233).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (234).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (235).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (236).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (237).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (238).png" alt=""><figcaption></figcaption></figure>
