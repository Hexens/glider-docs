---
description: >-
  Returns the list of builtin call names that are called from the instruction.
  E.g. keccak256, ecrecover...
---

# Instruction.builtin\_callee\_names()

`builtin_callee_names() → List[str]`

## Query Example

```python
from glider import *


def query():
  instructions = Instructions().with_callee_name("keccak256").exec(1)

  print(instructions[0].builtin_callee_names())

  return instructions
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-03 at 11.13.46 AM.png" alt=""><figcaption></figcaption></figure>

