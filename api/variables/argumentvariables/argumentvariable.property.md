---
description: >-
  Returns the position of the argument variable in the function signature. The
  index represents the argument variable's position, starting from
---

# ArgumentVariable.index

`property data: Dict`



## Query Example

```python
from glider import *

def query():

  functions = (
    Functions()
    .exec(1, 50)
    )

  for func in functions:
    args = func.arguments()
    print(f"Argument index: {args.list()[0].get_variable().index}")
  return functions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

