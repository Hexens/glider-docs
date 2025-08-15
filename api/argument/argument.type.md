---
description: Returns the type of the argument.
---

# Argument.type

_`property`_` ``type`_`: Type`_

## Query Example

```python
from glider import *


def query():
  functions = Functions().with_arg_count(2).exec(100)
 
  for f in functions:
    for arg in f.arguments().list():
        print(f"Argument type: {arg.get_variable().type}")

  return []
```

## Output Example

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-23 at 6.03.31 PM.png" alt=""><figcaption></figcaption></figure>
