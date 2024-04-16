---
description: >-
  Returns a list of the previous instructions of the current node in the control
  flow graph.
---

# Instruction.previous\_instructions()

`previous_instructions() → List[`[`Instruction`](./)`]`

The difference between the previous\_instructions() function and [previous\_instruction()](instruction.previous\_instruction.md) is that this function will return all previous instructions of the current instruction in the CFG (control-flow-graph).

_The function is intra-procedural, and thus will not follow function calls; for the **inter**-procedural variant of this function, use extended\_previous\_instructions()._

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
return c;
```

the function will return the instructions:

```solidity
uint256 c = a - b;
require(b <= a, errorMessage);
*entry_point_instruction*
```

Query

```python
from glider import *
def query():
  instructions = Instructions().exec(1,11)

  return instructions + instructions[0].previous_instructions()
```

Output

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
return c
},
...
"sol_instruction":solidity
uint256 c = a - b
},
...
"sol_instruction":solidity
require(b <= a, errorMessage)
},
"sol_instruction":solidity
{
        require(b <= a, errorMessage);
        uint256 c = a - b;
        return c;
    }
}
```



{% hint style="info" %}
As can be seen from the last output, "virtual" instructions like entry-point instruction, end-if, etc. when being printed with source\_code() will print full code block's source
{% endhint %}
