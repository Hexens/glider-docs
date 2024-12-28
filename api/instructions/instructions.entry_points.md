---
description: Returns an Instructions object for the 'entry point' instructions
---

# Instructions.entry\_point\_instructions()

`entry_point_instructions() →` [`Instructions`](./)

The [Instructions](./) object returned includes all entry points to functions.

## Query Example

```python
from glider import *

def query():
  
  return Instructions().entry_point_instructions().exec(1)
```

## Output Example

<figure><img src="../../.gitbook/assets/image (250).png" alt=""><figcaption></figcaption></figure>

As this returns the entry point to the function, the "sol\_instruction" field contains the function body.
