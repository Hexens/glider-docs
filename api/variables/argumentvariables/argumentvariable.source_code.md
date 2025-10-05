---
description: Returns the source code of the argument variable.
---

# ArgumentVariable.source\_code()

`source_code() → str`

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
    print(args.list()[0].get_variable().source_code())

  return functions
```

## Example Output

<figure><img src="../../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

