---
description: >-
  Returns true if the state variable is accessible in current contract,
  otherwise returns false. The state variable isn't accessible in current
  contract if it is a private inherited state variable
---

# StateVariable.is\_accessible()

`is_accessible() → bool`



## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(5, 10)
    .filter(lambda state_variable: state_variable.is_accessible())
  )

  print(state_variables[0].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
