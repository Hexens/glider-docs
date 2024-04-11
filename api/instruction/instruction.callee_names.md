---
description: >-
  Returns the list of function names that are called from the instruction. It
  returns an empty list for an instruction that does not call any functions
---

# Instruction.callee\_names()

Query

```python
from glider import *
def query():
  #fetch an instruction
  instruction = Instructions().exec(1,16)
  #print the list of function names called from the instruction
  print(instruction[0].callee_names()) 
  return []
```

Output

```
{"print_output": 
    [
        "['require']"
    ]
}
    
```
