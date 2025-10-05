---
description: Returns source code of variable
---

# Variable.source\_code()

`source_code() → str`

## Query Example

```python
from glider import *


def query():
  state_variables = (
    StateVariables()
    .exec(5)
  )

  print(state_variables[0].source_code())

  return state_variables
```

## Example Output

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

