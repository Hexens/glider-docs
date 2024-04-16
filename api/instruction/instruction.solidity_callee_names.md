---
description: >-
  Returns the list of solidity function names that are called from the
  instruction. Returns a empty list if the instruction does not call any
  solidity function.
---

# Instruction.solidity\_callee\_names()

`solidity_callee_names() → List[str]`

Like [callee\_names()](instruction.callee\_names.md) the function return list of called function names, but filtered to only built-in functions, like `require, assert, keccak256` etc.

Query

```python
from glider import *
def query():
  #fetch a list of instructions
  instructions = Instructions().exec(1,17) 
  for instruction in instructions:
    #print the names of solidity functions that are called from the instruction
    print(instruction.solidity_callee_names())
  return instructions
```

Output

```solidity
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function mul(uint256 a, uint256 b) internal pure returns (uint256) {
        if (a == 0) {
            return 0;
        }
        uint256 c = a * b;
        require(c / a == b, "SafeMath: multiplication overflow");
        return c;
    }
"sol_instruction":solidity
require(c / a == b, "SafeMath: multiplication overflow")
},
"root":{1 item
    "print_output":[1 item
    0:string"['require']"
    ]
}
```

