---
description: Returns break instructions of the function/modifier.
---

# Callable.break\_instructions()

`break_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  results = []
  for function in functions:
    # For each function, return each break instruction
    for instruction in function.break_instructions().exec():
      results.append(instruction)

  return results
```

## Example output

```solidity
"root":{4 items
"contract":string"0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
"contract_name":string"Strings"
"sol_function":solidity
function toString(uint256 value) internal pure returns (string memory) {
        unchecked {
            uint256 length = Math.log10(value) + 1;
            string memory buffer = new string(length);
            uint256 ptr;
            /// @solidity memory-safe-assembly
            assembly {
                ptr := add(buffer, add(32, length))
            }
            while (true) {
                ptr--;
                /// @solidity memory-safe-assembly
                assembly {
                    mstore8(ptr, byte(mod(value, 10), _SYMBOLS))
                }
                value /= 10;
                if (value == 0) break;
            }
            return buffer;
        }
    }
"sol_instruction":solidity
break
}
```
