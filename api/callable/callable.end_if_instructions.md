---
description: Returns end_if instructions of the function/modifier.
---

# Callable.end\_if\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  conditional = []
  for function in functions:
    for if_instruction in function.end_if_instructions():
      # For each function, return the conditional (if) instructions
      conditional.append(if_instruction)

  return conditional
```

## Example output

```json
[
  {
    "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
    "contract_name": "Pausable",
    "sol_function": `
    // Formatted for the example
    function setPaused(bool _paused) external onlyOwner {
        if (_paused == paused) {
            return;
        }

        paused = _paused;

        if (paused) {
            lastPauseTime = block.timestamp;
        }

        emit PauseChanged(paused);
    }
    `,
    "sol_instruction": `
    // Formatted for the example
    if (_paused == paused) {
        return;
    }
    `,
  },
  {
    ...
    "sol_instruction": `
    // Formatted for the example
    if (paused) {
        lastPauseTime = block.timestamp;
    }
    `,
  }
  ...
]
```
