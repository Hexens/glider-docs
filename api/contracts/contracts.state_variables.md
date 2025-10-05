---
description: Returns the State Variables object for the state variables of the contracts.
---

# Contracts.state\_variables()

`state_variables() →` [`StateVariables`](../statevariables/)

## Query Example

```python
from glider import *


def query():
    state_variables = (
        Contracts()
        .with_name("Manager")
        .exec(1)
        .state_variables()
        .exec()
    )

    return state_variables
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-17 at 11.03.22 AM.png" alt=""><figcaption></figcaption></figure>
