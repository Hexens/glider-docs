---
description: >-
  Returns true if the instruction is placeholder instruction, otherwise returns
  false. A placeholder instruction is generally found in modifiers
---

# Instruction.is\_placer()

Query

```python
from glider import *
def query():
  placers = []
  #fetch a list of instructions
  instructions = Instructions().exec(600)
  for instruction in instructions:
    #check if instruction is a placeholder instruction
    if(instruction.is_placer()):
      placers.append(instruction)  
  return placers
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "modifier onlyOwner() {\n        require(owner() == _msgSender(),\"Ownable: caller is not the owner\");\n        _;\n    }",
  "sol_instruction": "_"
}
```
