---
description: Returns true if the state variable is constant, otherwise returns false.
---

# StateVariable.is\_constant()

`is_constant() → bool`



## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(20)
    .filter(lambda state_variable: state_variable.is_constant())
  )

  print(state_variables[0].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
