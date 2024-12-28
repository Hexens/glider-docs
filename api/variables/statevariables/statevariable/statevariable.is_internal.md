---
description: >-
  Returns true if the visibility of the state variable is internal, otherwise
  returns false.
---

# StateVariable.is\_internal()

`is_internal() → bool`

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(20)
    .filter(lambda state_variable: state_variable.is_internal())
  )

  print(state_variables[0].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

