---
description: Returns true if it is ">=" check, otherwise returns false.
---

# Condition.is\_geq()

```python
from glider import *

def query():
  if_instructions = Instructions().if_instructions().exec(100)

  for if_instruction in if_instructions:
    if if_instruction.get_condition().is_geq():
      print(if_instruction.source_code())
      return [if_instruction.get_parent()]
  return []
```



Output:

```solidity
"root":{3 items
"contract":string"0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
"contract_name":string"SignedMath"
"sol_function":solidity
function abs(int256 n) internal pure returns (uint256) {
        unchecked {
            // must be unchecked in order to support `n = type(int256).min`
            return uint256(n >= 0 ? n : -n);
        }
    }
},
"root":{1 item
"print_output":[1 item
0:string"return uint256(n >= 0 ? n : -n)"
]
}
```
