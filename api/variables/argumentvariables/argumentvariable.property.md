---
description: >-
  Returns the position of the argument variable in the function signature. The
  index represents the argument variable's position, starting from 0.
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

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 4.54.58 PM.png" alt=""><figcaption></figcaption></figure>
