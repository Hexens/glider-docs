---
description: >-
  Returns true if the instruction is  an expression instruction, otherwise
  returns false.
---

# Instruction.is\_expression()

Query

```python
from glider import *
def query():
  expressions = []
  #fetch a list of instructions
  instructions = Instructions().exec(10)
  for instruction in instructions:
    #check if instruction is an expression instruction
    if(instruction.is_expression()):
      expressions.append(instruction)  
  return expressions
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "constructor() {\n        _setOwner(_msgSender());\n    }",
  "sol_instruction": "_setOwner(_msgSender())"
}
```
