---
description: >-
  Returns true if the instruction has an external dependency on external
  variables, false otherwise.
---

# Instruction.has\_global\_df()

`has_global_df() → bool`

By default, global dataflow sources are considered to be global variables like `msg.sender, msg.data, tx.origin`, and the arguments of external/public functions.

The function works in an inter-procedural manner (works recursively on the bigger data-flow graph).

## Query Example

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().exec(5)
  results = []
  #check if the instruction has a dependency on a global variable
  for instruction in instructions:
    if instruction.has_global_df():
      results.append(instruction)
  return results
```

## Output

```solidity
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Context"
"sol_function":solidity
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
"sol_instruction":solidity
return msg.sender
},
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
uint256 c = a + b
},
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
```

