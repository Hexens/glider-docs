---
description: >-
  Returns true if the instruction is entry_point instruction, otherwise returns
  false.
---

# Instruction.is\_entry\_point()

Query

```python
from glider import *
def query():
  ifs = []
  #fetch a list of instructions
  instructions = Instructions().exec(3)
  for instruction in instructions:
    #check if instruction is an if instruction
    if(instruction.is_if()):
      ifs.append(instruction)  
  return ifs
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context",
  "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }",
  "sol_instruction": "{\n        return msg.sender;\n    }"
}

{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context",
  "sol_function": "function _msgData() internal view virtual returns (bytes calldata) {\n        return msg.data;\n    }",
  "sol_instruction": "{\n        return msg.data;\n    }"
}
```
