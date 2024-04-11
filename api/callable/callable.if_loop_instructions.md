---
description: Returns if_loop instructions of the function/modifier.
---

# Callable.if\_loop\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().with_modifiers_name_not(["onlyOwner"]).exec(100)

  if_loop_instructions = []
  for function in functions:
    # For each function without an "onlyOwner" modifier, return the if loop instructions
    for instruction in function.if_loop_instructions():
      if_loop_instructions.append(instruction)

  return if_loop_instructions
```

## Example output

```json
[
  {
    "contract": "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23",
    "contract_name": "WadRayMath",
    "sol_function": `
    // Formatted for the example
    function rayPow(uint256 x,uint256 n) internal pure returns (uint256 z) {
        z = n % 2 != 0 ? x : _RAY;

        for (n /= 2; n != 0; n /= 2) {
            x = rayMul(x,x);

            if (n % 2 != 0) {
                z = rayMul(z,x);
            }
        }
    }
    `,
    "sol_instruction": "n != 0"
  },
  ...
]
```
