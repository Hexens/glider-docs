---
description: Returns true if the state variable is immutable, otherwise returns false.
---

# StateVariable.is\_immutable()

`is_immutable() → bool`



## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(175)
    .filter(lambda state_variable: state_variable.is_immutable())
  )

  print(state_variables[0].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

