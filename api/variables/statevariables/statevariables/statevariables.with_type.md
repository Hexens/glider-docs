---
description: Adds a filter to get state variables that have the given type.
---

# StateVariables.with\_type()

`with_type(variable_type: str) →` [`StateVariables`](../)

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .with_type("mapping(uint256 => uint256)")
    .exec(5)
  )

  print(state_variables[0].source_code())
  print(state_variables[1].source_code())

  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
