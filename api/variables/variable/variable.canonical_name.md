---
description: Returns the canonical name of the variable.
---

# Variable.canonical\_name

`property canonical_name: str`

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(5)
  )

  print(state_variables[0].canonical_name)

  return state_variables
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

