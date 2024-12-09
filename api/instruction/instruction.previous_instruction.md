---
description: Returns a list of immediate previous instructions in the control flow graph.
---

# Instruction.previous\_instruction()

`previous_instruction() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](./)`]`

The difference between the previous\_instruction() function and [previous\_instructions()](instruction.previous_instructions.md) is that this function will return a list of immediate previous instructions of the current instruction in the CFG (control-flow-graph).

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
return c;
```

the function will return the instruction:

```solidity
uint256 c = a - b;
```

## Query Example

```python
from glider import *
def query():
  instructions = Instructions().exec(1,11)

  return instructions + list(instructions[0].previous_instruction())
```

## Output Example

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



{% hint style="info" %}
The function returns APISet, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
