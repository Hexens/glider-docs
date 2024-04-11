---
description: >-
  Returns the list of solidity function names that are called from the
  instruction. Returns a empty list if the instruction does not call any
  solidity function.
---

# Instruction.solidity\_callee\_names()

Query

```python
from glider import *
def query():
  #fetch a list of instructions
  instructions = Instructions().exec(2,16) 
  for instruction in instructions:
    #print the names of solidity functions that are called from the instruction
    print(instruction.solidity_callee_names())
  return []
```

Output

```json
{"print_output": 
    [
        "['require']", 
        "[]"
    ]
}
```

