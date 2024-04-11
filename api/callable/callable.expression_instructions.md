---
description: Returns expression instructions of the function/modifier.
---

# Callable.expression\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  expressions = []
  for function in functions:
    for exp_instruction in function.expression_instructions():
      # For each function, return the expressions
      expressions.append(exp_instruction)

  return expressions
```

## Example output

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": `
    // Formatted for the example
    constructor() {
        _setOwner(_msgSender());
    }
    `,
    "sol_instruction": "_setOwner(_msgSender())"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": `
    // Formatted for the example
    function renounceOwnership() public virtual onlyOwner {
        _setOwner(address(0));
    }
    `,
    "sol_instruction": "_setOwner(address(0))"
  },
  ...
]
```
