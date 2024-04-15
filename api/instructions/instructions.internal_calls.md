---
description: >-
  Returns a list of all internal call instructions if the parameter is skipped.
  Otherwise, returns call instructions of corresponding type (internal, public
  or private)
---

# Instructions.internal\_calls()

`internal_calls(visibility: str = '') →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().if_loop_instructions().exec(1)

  return instructions
```

## Output Example

```solidity
{
    "contract": "0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
    "contract_name": "Strings"
    "sol_function":
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
    "sol_instruction":
        true
}
```
