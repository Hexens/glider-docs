---
description: Adds a filter to get state variables that have all given properties
---

# StateVariables.with\_all\_properties()

`with_all_properties(properties: List[`[`StateVariableProp`](../statevariableprop.md)`]) →` [`StateVariables`](./)

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .with_all_properties([StateVariableProp.CONSTANT, StateVariableProp.PUBLIC])
    .exec(10)
  )

  print(state_variables[0].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

