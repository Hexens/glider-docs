---
description: Returns true if it is "<" check, otherwise returns false.
---

# Condition.is\_le()

## Query Example

```python
from glider import *

def query():

  instructions = Functions().with_name("min").exec(1).instructions().if_instructions().exec(1)
  print(instructions[0].get_condition().is_le())

  return instructions
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (219).png" alt=""><figcaption></figcaption></figure>
