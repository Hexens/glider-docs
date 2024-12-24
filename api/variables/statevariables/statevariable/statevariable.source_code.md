---
description: Returns the source code of the state variable.
---

# StateVariable.source\_code()

`source_code() → str`

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(5)
  )

  for state_var in state_variables:
    print(state_var.source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

