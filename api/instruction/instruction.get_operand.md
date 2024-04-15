---
description: Returns the index-th operand of the instruction
---

# Instruction.get\_operand()

`get_operand(`_`index: int`_`) → Value`

The instruction consists of operands, which are typed as Value or Value-derived objects, such as Var, Call, etc.&#x20;

Query

```python
from glider import *
def query():
  instruction = Instructions().exec(1,1)
  operand = instruction[0].get_operand(0)
  if isinstance(operand,Var):
    print(operand.type().name)
    print(operand.expression)
  return instruction
```

Output

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
"root":{1 item
        "print_output":[2 items
        0:string"address"
        1:string"msg.sender"
        ]
}
```
