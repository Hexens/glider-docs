---
description: Returns the source code of the argument.
---

# Argument.source\_code()

`source_code() → str`

## Query Example

```python
from glider import *

def query():
  functions = Functions().exec(100)

  for f in functions:
    for arg in f.arguments().list():
      print(f"Argument Source code: {arg.source_code()}")

  return []
```

## Output Example

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-23 at 5.29.15 PM.png" alt=""><figcaption></figcaption></figure>
