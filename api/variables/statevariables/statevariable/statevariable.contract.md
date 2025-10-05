---
description: Returns state variable's parent contract if it exists.
---

# StateVariable.contract()

`contract() →` [`Contract`](../../../contract/) `|` [`NoneObject`](../../../internal/noneobject/)

## Query Example

```python
from glider import *


def query():
  return [
    state_var.contract()
    for state_var 
    in StateVariables().exec(10,10)
  ]
```

## Example Output

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-09-23 at 18.59.20.png" alt=""><figcaption></figcaption></figure>
