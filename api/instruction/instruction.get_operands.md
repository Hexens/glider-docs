---
description: Returns all of the instruction operands
---

# Instruction.get\_operands()

`get_operands() → List[Value]`

The instruction consists of operands, which are typed as Value or Value-derived objects, such as Var, Call, etc.&#x20;

Note that the function returns first-level operands; if the instruction has complex expressions, which on their own have operands, the function will not return those. Although the function can be used to get their operands as well when called on the value.

## Query Example

```python
from glider import *
def query():
  instruction = Instructions().exec(1,1)
  operands = instruction[0].get_operands()

  for operand in operands:
    if isinstance(operand,Var):
      print(operand.type().name)
      print(operand.expression)
      
  return instruction
```

## Output

```json
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
