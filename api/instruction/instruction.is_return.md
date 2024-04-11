---
description: >-
  Returns true if the instruction is return instruction, otherwise returns
  false.
---

# Instruction.is\_return()

Query

```python
from glider import *
def query():
  returns = []
  #fetch a list of instructions
  instructions = Instructions().exec(3)
  for instruction in instructions:
    #check if instruction is a return instruction
    if(instruction.is_return()):
      returns.append(instruction)  
  return returns
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context",
  "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }",
  "sol_instruction": "return msg.sender"
}
```
