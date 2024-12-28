---
description: >-
  Returns an Instructions object for the instructions that are from assembly
  block.
---

# Instructions.asm\_block\_instructions()

`asm_block_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():

  return Instructions().asm_block_instructions().exec(2, 2)
```

## Output Example

<figure><img src="../../.gitbook/assets/image (239).png" alt=""><figcaption></figcaption></figure>
