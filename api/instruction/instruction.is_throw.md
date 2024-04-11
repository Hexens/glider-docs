---
description: Returns True if the instruction is throw instruction, otherwise returns False.
---

# Instruction.is\_throw()

Query

```python
from glider import *
def query():
  throws = []
  #fetch a list of instructions
  instructions = Instructions().exec(3)
  for instruction in instructions:
    #check if instruction is a throw instruction
    if(instruction.is_throw()):
      throws.append(instruction)
    #print the return value from is_throw()
    print(instruction.is_throw())  
  return throws
```

Output

```json
{
  "print_output": [
    "False",
    "False",
    "False"
  ]
}
```

The query could not find any throw instructions, hence it prints False
