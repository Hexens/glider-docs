---
description: Returns true if it is ">=" check, otherwise returns false.
---

# Condition.is\_geq()

## Query Example

```python
from glider import *

def query():

  instructions = Functions().with_name("log10").exec(1).instructions().if_instructions().exec(1)

  print(instructions[0].get_condition().is_geq())

  return instructions
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (217).png" alt=""><figcaption></figcaption></figure>
