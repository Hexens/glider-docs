---
description: Returns the list of the state variable's properties.
---

# StateVariable.properties()

`properties() → List[str]`

## Query Example

```python
from glider import *


def query():
  state_variables = (
    StateVariables()
    .exec(1)
  )

  print(state_variables[0].properties())

  return state_variables
```

## Example Output

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



