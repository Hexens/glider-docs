---
description: Returns entry_point instructions of the function/modifier.
---

# Callable.entry\_point\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  entry_points = []
  for function in functions:
    for entry_point_instruction in function.entry_point_instructions():
      # For each function, return entry points
      entry_points.append(entry_point_instruction)

  return entry_points
```

## Example output

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": `
    // Formatted for the example
    function _msgData() internal view virtual returns (bytes calldata) {
        return msg.data;
    }
    `,
    "sol_instruction": `
    // Formatted for the example
    {
        return msg.data;
    }
    `
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": `
    // Formatted for the example
    constructor() {
        _setOwner(_msgSender());
    }
    `,
    "sol_instruction": `
    // Formatted for the example
    {
        _setOwner(_msgSender());
    }
    `
  },
  ...
]
```
