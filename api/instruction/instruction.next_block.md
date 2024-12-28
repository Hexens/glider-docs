---
description: >-
  Returns the list of instructions following the current instruction till the
  branching point.
---

# Instruction.next\_block()

`next_block() →` [`APIList`](../iterables/apilist.md)`[`[`Instruction`](./)`]`

## Query Example

```python
from glider import *

def query():
  ins = Instructions().start_asm_instructions().exec(1)

  return ins + ins[0].next_block()
```

## Output Example

### Virtual instruction, that represent asm start block

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Next block instructions:

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>
