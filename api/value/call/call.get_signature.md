---
description: Returns the signature of the function being called
hidden: true
---

# Call.get\_signature()

`get_signature() → str`

**Query Example**

```python
from glider import *

def query():
  instructions = Instructions().calls().exec(2)

  for entry_ins in instructions:
    for call in entry_ins.get_callee_values():
        print(call.get_signature(), call.expression)

  return instructions
```

**Output**

```solidity
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function add(uint256 a, uint256 b) internal pure returns (uint256) {
        uint256 c = a + b;
        require(c >= a, "SafeMath: addition overflow");
        return c;
    }
"sol_instruction":solidity
require(c >= a, "SafeMath: addition overflow")
}
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function sub(uint256 a, uint256 b) internal pure returns (uint256) {
        return sub(a, b, "SafeMath: subtraction overflow");
    }
"sol_instruction":solidity
return sub(a, b, "SafeMath: subtraction overflow")
}
"root":{1 item
"print_output":[4 items
0:string"require(bool,string)"
1:string"require(bool,string)(c >= a,"SafeMath: addition overflow")"
2:string"sub(uint256,uint256,string)"
3:string"sub(a,b,"SafeMath: subtraction overflow")"
]
}
```
