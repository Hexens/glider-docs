---
description: Returns end_loop instructions of the function/modifier.
---

# Callable.end\_loop\_instructions()

`end_loop_instructions() →` [`Instructions`](../instructions/)

The functions will return end\_loop instructions for all types of loops e.g. while/for

end\_loop instruction is not a "real" instruction but rather an abstract one representing the end of the loop.

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  loop = []
  for function in functions:
    for loop_instruction in function.end_loop_instructions().exec():
      # For each function, return the loop instructions
      loop.append(loop_instruction)

  return loop
```

## Example output

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Strings",
    "sol_function": `
    // Formatted for the example
    function toString(uint256 value) internal pure returns (string memory) {
        if (value == 0) {
            return "0";
        }

        uint256 temp = value;
        uint256 digits;

        while (temp != 0) {
            digits++;
            temp /= 10;
        }

        bytes memory buffer = new bytes(digits);
        while (value != 0) {
            digits -= 1;
            buffer[digits] = bytes1(uint8(48 + uint256(value % 10)));
            value /= 10;
        }

        return string(buffer);
    }
    `,
    "sol_instruction": `
    // Formatted for the example
    while (temp != 0) {
        digits++;
        temp /= 10;
    }
    `,
  },
  ...
]
```
