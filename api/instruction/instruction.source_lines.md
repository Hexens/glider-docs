---
description: Returns the corresponding source line numbers of a instruction
---

# Instruction.source\_lines()

Query

```python
from glider import *
def query():
  #fetch a list of instructions
  instructions = Instructions().exec(1) 
  #print the corresponding source line numbers of the instruction
  print(instructions[0].source_lines())
  return []
```

Output

```json
{
  "print_output": [
    "[19, 20, 21]"
  ]
}
```
