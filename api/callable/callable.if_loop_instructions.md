---
description: Returns if_loop instructions of the function/modifier.
---

# Callable.if\_loop\_instructions()

The function returns [Instructions](../instructions/) that represent the condition part in loop operators. It will return for all types of loops e.g. while and for

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().without_modifier_names(["onlyOwner"]).exec(100)

  if_loop_instructions = []
  for function in functions:
    # For each function without an "onlyOwner" modifier, return the if loop instructions
    for instruction in function.if_loop_instructions().exec():
      if_loop_instructions.append(instruction)

  return if_loop_instructions
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
true
}
"root":{4 items
"contract":string"0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
"contract_name":string"Strings"
"sol_function":solidity
function toHexString(uint256 value, uint256 length) internal pure returns (string memory) {
        bytes memory buffer = new bytes(2 * length + 2);
        buffer[0] = "0";
        buffer[1] = "x";
        for (uint256 i = 2 * length + 1; i > 1; --i) {
            buffer[i] = _SYMBOLS[value & 0xf];
            value >>= 4;
        }
        require(value == 0, "Strings: hex length insufficient");
        return string(buffer);
    }
"sol_instruction":solidity
i > 1
}
```
