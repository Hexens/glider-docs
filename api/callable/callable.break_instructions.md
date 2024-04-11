---
description: Returns break instructions of the function/modifier.
---

# Callable.break\_instructions()

## Return type

→ List\[[Instruction](../instruction/)]

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  results = []
  for function in functions:
    # For each function, return each break instruction
    for instruction in function.break_instructions():
      results.append(instruction)

  return results
```

## Example output

```json
[
  {
    "contract": "0x0000000000000000000000000000000000000001",
    "contract_name": "MockContract",
    // Formatted for the example
    "sol_function": `
    function functionWithBreak(uint256 _length, uint256 _index) external {
        require(_index < _length, "Index out of bounds");
        for (uint256 i = 0; i < _length; i++) {
            if (i == _index) {
                break;
            }
        }
    }
    `,
    "sol_instruction": "break"
  },
  ...
]
```
