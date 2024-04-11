---
description: Returns an Instructions object for the instructions of the function/modifier.
---

# Callable.instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(1)

  instructions = []
  for instruction in functions[0].instructions().exec():
    # Return an array of all instructions for a function
    instructions.append(instruction)

  return instructions
```

## Example output

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "function renounceOwnership() public virtual onlyOwner {\\n        _setOwner(address(0));\\n    }",
    "sol_instruction": "_setOwner(address(0))"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "function renounceOwnership() public virtual onlyOwner {\\n        _setOwner(address(0));\\n    }",
    "sol_instruction": "onlyOwner"
  }
]
```
