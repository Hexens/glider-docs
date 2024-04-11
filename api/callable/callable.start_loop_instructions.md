---
description: Returns start_loop instructions of the function/modifier.
---

# Callable.start\_loop\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  loop_instructions = []
  for function in functions:
    for instruction in function.start_loop_instructions():
      # Return the starting loop instructions for each function
      loop_instructions.append(instruction)

  return loop_instructions
```

## Example output

```json
[
  {
    "contract": "0x27A05e7a40F2d980F8853e94c3cE54C70e68527D",
    "contract_name": "Strings",
    "sol_function": `
    // Formatted for the example
    function toHexString(uint256 value) internal pure returns (string memory) {
        if (value == 0) {
            return "0x00";
        }

        uint256 temp = value;
        uint256 length = 0;

        while (temp != 0) {
            length++;
            temp >>= 8;
        }

        return toHexString(value,length);
    }
    `,
    "sol_instruction": `
    // Formatted for the example
    while (temp != 0) {
        length++;
        temp >>= 8;
    }
    `
  },
  ...
]
```
