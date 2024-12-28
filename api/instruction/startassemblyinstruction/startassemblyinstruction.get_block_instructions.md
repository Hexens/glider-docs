---
description: Returns all instructions from the assembly block
---

# StartAssemblyInstruction.get\_block\_instructions()

`get_block_instructions() →` [`APIList`](../../iterables/apilist.md)`[`[`Instruction`](../)`]`

## Query Example

```python
from glider import *

def query():
    assembly_instructions = Functions().exec(1,57).start_asm_instructions().exec()

    return assembly_instructions + assembly_instructions[0].get_block_instructions()
```

## Example Output

<figure><img src="../../../.gitbook/assets/image (223).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (225).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (226).png" alt=""><figcaption></figcaption></figure>
