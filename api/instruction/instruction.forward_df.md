---
description: >-
  Returns a list of all instructions following the current node in the current
  data flow graph. It returns 0 for an instruction that does not have any
  following instructions.
---

# Instruction.forward\_df()

Query

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().exec(1,16)
  # return the list of instructions following the current instruction
  return instructions[0].forward_df()
```

Output

```python
{
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD", 
    "contract_name": "Ownable", 
    "sol_function": "function transferOwnership(address newOwner) public virtual onlyOwner {\n        require(newOwner != address(0),\"Ownable: new owner is the zero address\");\n        _setOwner(newOwner);\n    }", 
    "sol_instruction": "require(newOwner != address(0),\"Ownable: new owner is the zero address\")"
}
```
