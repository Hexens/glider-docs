---
description: Returns the list of all state variables of the contract.
---

# Contract.state\_variables()

`state_variables() →` [`StateVariables`](../statevariables/)

Returns a StateVariables object for the state variables of the contract.

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1)

  state_variables = contracts[0].state_variables().exec()
  for state_variable in state_variables:
    print(state_variable.source_code())

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>
