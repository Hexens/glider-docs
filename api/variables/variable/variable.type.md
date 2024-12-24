---
description: Returns the type of the variable.
---

# Variable.type

`property type: Type`

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(5)
  )

  print(state_variables[0].type)

  return state_variables
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
