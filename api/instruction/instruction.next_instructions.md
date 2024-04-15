---
description: >-
  Returns a list of all instructions following the current node in the control
  flow graph.
---

# Instruction.next\_instructions()

`next_instructions() → List[`[`Instruction`](./)`]`

The  difference between the next\_instruction**S**() function and [next\_instruction()](instruction.next\_instruction.md) is that this function will return all instructions following the current instruction in the CFG (control-flow-graph).

_The function is intra-procedural, and thus will not follow function calls; for the **inter**-procedural variant of this function, use extended\_next\_instructions()._

### Query Example

```python
from glider import *
def query():
  instructions = Instructions().exec(1,9)

  return instructions + instructions[0].next_instructions()
```

### Output

```solidity
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function sub(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        require(b <= a, errorMessage);
        uint256 c = a - b;
        return c;
    }
"sol_instruction":solidity
require(b <= a, errorMessage)
},
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function sub(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        require(b <= a, errorMessage);
        uint256 c = a - b;
        return c;
    }
"sol_instruction":solidity
uint256 c = a - b
},
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function sub(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        require(b <= a, errorMessage);
        uint256 c = a - b;
        return c;
    }
"sol_instruction":solidity
return c
}
```
