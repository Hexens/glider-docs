---
description: >-
  Returns an Instructions object for the call instructions of the
  function/modifier.
---

# Callable.calls\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  calls_instructions = []
  for function in functions:
    # List all call instructions in the given functions
    for instruction in function.calls_instructions().exec():
      calls_instructions.append(instruction)

  return calls_instructions
```

## Example output

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "constructor() {\\n        _setOwner(_msgSender());\\n    }",
    "sol_instruction": "_setOwner(_msgSender())"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "constructor() {\\n        _setOwner(_msgSender());\\n    }",
    "sol_instruction": "_setOwner(_msgSender())"
  },
  ...
]
```
