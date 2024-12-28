---
description: Returns true if it is an equality check, otherwise returns false.
---

# Condition.is\_eq()

`is_eq() -> bool`

## Query Example

```python
from glider import *

def query():
  instructionlist = Instructions().if_instructions().exec(1)
  
  condition = instructionlist[0].get_condition()
  print(condition.is_eq())
  return instructionlist
```

Outputs:

<figure><img src="../../../../.gitbook/assets/image (216).png" alt=""><figcaption></figcaption></figure>
