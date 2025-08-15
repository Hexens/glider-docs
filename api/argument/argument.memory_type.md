---
description: Returns the memory type of the argument
---

# Argument.memory\_type

_`property`_` ``memory_type:`` `_`str`_

## Query Example

```python
from glider import *


def query():
  functions = Functions().with_arg_count(2).exec(100)
 
  for f in functions:
    for arg in f.arguments().list():
        print(f"Argument: {arg.get_variable().name} - {arg.get_variable().memory_type}")

  return []
```

## Output Example

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-23 at 6.03.31 PM (1).png" alt=""><figcaption></figcaption></figure>
