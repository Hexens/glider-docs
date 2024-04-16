---
description: Returns a list of immediate following instructions in the control flow graph.
---

# Instruction.next\_instruction()

`next_instruction() → List[`[`Instruction`](./)`]`

The difference between the next\_instruction() function and [next\_instructions()](instruction.next\_instructions.md) is that this function will return a list of instructions that are immediately following the current instruction in the CFG (control-flow-graph).

_The function is intra-procedural._



For example, in the function:

```solidity
function sub(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        require(b <= a, errorMessage);
        uint256 c = a - b;
        return c;
    }
```

for the instruction:&#x20;

```solidity
require(b <= a, errorMessage);
```

the function will return the instruction:

```solidity
uint256 c = a - b;
```

## Query Example

```python
from glider import *
def query():
  instructions = Instructions().exec(1,9)

  return instructions + instructions[0].next_instruction()
```

## Output

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
}
```

