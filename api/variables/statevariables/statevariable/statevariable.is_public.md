---
description: >-
  Returns true if the visibility of the state variable is public, otherwise
  returns false.
---

# StateVariable.is\_public()

`is_public() → bool`

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(30)
    .filter(lambda state_variable: state_variable.is_public())
  )

  print(state_variables[0].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

