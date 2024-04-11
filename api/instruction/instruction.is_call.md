---
description: Returns True if the instruction is call instruction, otherwise returns False.
---

# Instruction.is\_call()

Query

```python
from glider import *
def query():
  calls = []
  #fetch a list of instructions
  instructions = Instructions().exec(10) 
  for instruction in instructions:
    if(instruction.is_call()):
      calls.append(instruction)  
  return calls
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
