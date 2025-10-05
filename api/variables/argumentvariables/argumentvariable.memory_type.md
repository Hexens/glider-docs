---
description: Returns the memory type of the argument variable.
---

# ArgumentVariable.memory\_type

`property memory_type: str`

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
    print(f"Memory type: {args.list()[0].get_variable().memory_type}")

  return functions
```

## Example Output

<figure><img src="../../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

