---
description: Returns true if it is "<=" check, otherwise returns false.
---

# Condition.is\_leq()

## Query Example

```python
from glider import *

def query():

  instructions = Functions().with_name("processProof").exec(1,1).instructions().if_instructions().exec(1)
  print(instructions[0].get_condition().is_leq())

  return instructions
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (220).png" alt=""><figcaption></figcaption></figure>
