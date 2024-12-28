---
description: Adds a filter to get state variables with the given name
---

# StateVariable.with\_name()

`with_name(name: str, sensitivity: bool = True) →` [`StateVariables`](./)

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .with_name("owner")
    .exec(5)
  )

  print(state_variables[0].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

