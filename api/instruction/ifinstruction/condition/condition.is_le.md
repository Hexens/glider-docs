---
description: Returns true if it is "<" check, otherwise returns false.
---

# Condition.is\_le()

```python
from glider import *

def query():
  if_instructions = Instructions().if_instructions().exec(100)

  for if_instruction in if_instructions:
    if if_instruction.get_condition().is_le():
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
function min(int256 a, int256 b) internal pure returns (int256) {
        return a < b ? a : b;
    }
},
"root":{1 item
"print_output":[1 item
0:string"return a < b ? a : b"
]
}
```
