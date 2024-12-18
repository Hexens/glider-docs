---
description: Executes the formed query and returns the list of StateVariable objects.
---

# StateVariables.exec()

`exec(limit_count: int = 0, offset_count: int = 0) ->` [`APIList`](../../../iterables/apilist.md)`[`[`StateVariable`](../statevariable.md)`]`

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(5, 5)
  )
  return state_variables
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
