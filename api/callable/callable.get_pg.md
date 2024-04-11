---
description: Constructs and returns procedure graph of the function/modifier.
---

# Callable.get\_pg()

## Return type

→ ProcedureGraph

## Example

```python
from glider import *
def query():
  functions = Functions().with_modifiers_name_not(["onlyOwner"]).exec(100)

  state_variables = []
  for function in functions:
    # For each function without an "onlyOwner" modifier, return all state variables in the procedure graph
    for state_var in function.get_pg().get_state_variables():
      state_variables.append(state_var.to_json())

  return state_variables
```

## Example output

```json
[
  { "id": -2, "node": "Ownable._owner", "type": "state_variable" },
  { "id": -8, "node": "VRFConsumerBase.nonces", "type": "state_variable" },
  { "id": -7, "node": "VRFConsumerBase.vrfCoordinator", "type": "state_variable" },
  { "id": -6, "node": "VRFConsumerBase.LINK", "type": "state_variable" }
]
```
