---
description: Returns true if it is a non-equality check, otherwise returns false.
---

# Condition.is\_neq()

`is_neq() → bool`

## Query Example

```python
from glider import *


def query():
  instructions = (
    Instructions()
    .if_instructions()
    .exec(100)
    .filter(lambda instruction : instruction.get_condition().is_neq())
  )

  return instructions
```

## Example Output

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-03 at 1.44.15 PM.png" alt=""><figcaption></figcaption></figure>
