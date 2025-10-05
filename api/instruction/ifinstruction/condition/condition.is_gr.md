---
description: Returns true if it is ">" check, otherwise returns false.
---

# Condition.is\_gr()

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().if_instructions().exec(10).filter(lambda instruction : instruction.get_condition().is_gr())

  return instructions
```

## Output Example

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-03 at 1.42.09 PM.png" alt=""><figcaption></figcaption></figure>
