---
description: Returns the source code of the instruction
---

# Instruction.source\_code()

Query

```python
from glider import *
def query():
  #fetch a list of instructions
  instructions = Instructions().exec(1) 
  #print the source code of the instruction
  print(instructions[0].source_code())
  return []
```

Output

```json
{
  "print_output": [
    "{\n        return msg.sender;\n    }"
  ]
}
```
