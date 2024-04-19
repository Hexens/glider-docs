---
description: Returns the Functions object for the functions of the contracts.
---

# Contracts.functions()

`functions() →` [`Functions`](../function/)



## Example Query

```python
from glider import *

def query():

  functions = Contracts().functions().exec(1)

  return functions
```

## Output Example

```solidity
{
    "contract": "0x209adb20b0d6115ea69ef34c7afa4ac6216c2be2"
    "contract_name": "Strings"
    "sol_function":
        function toString(uint256 value) internal pure returns (string memory) {
            // Inspired by OraclizeAPI's implementation - MIT licence
            // https://github.com/oraclize/ethereum-api/blob/b42146b063c7d6ee1358846c198246239e9360e8/oraclizeAPI_0.4.25.sol

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
            uint256 index = digits - 1;
            temp = value;
            while (temp != 0) {
                buffer[index--] = byte(uint8(48 + temp % 10));
                temp /= 10;
            }
            return string(buffer);
    }

}
```
