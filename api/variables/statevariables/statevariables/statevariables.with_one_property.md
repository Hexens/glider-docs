---
description: >-
  Adds a filter to get state variables that at least have one of the given
  properties.
---

# StateVariables.with\_one\_property()

`with_one_property(properties: List[`[`StateVariableProp`](../statevariableprop.md)`]) →` [`StateVariables`](./)



## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .with_one_property([StateVariableProp.PRIVATE, StateVariableProp.PUBLIC])
    .exec(5)
  )

  print(state_variables[0].source_code())
  print(state_variables[1].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

