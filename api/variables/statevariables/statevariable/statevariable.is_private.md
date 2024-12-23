---
description: >-
  Returns true if the visibility of the state variable is private, otherwise
  returns false.
---

# StateVariable.is\_private()

`is_private() → bool`

## Query Example&#x20;

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(20)
    .filter(lambda state_variable: state_variable.is_private())
  )

  print(state_variables[0].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

