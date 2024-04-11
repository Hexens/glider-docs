---
description: >-
  Returns a list of all previous instructions of the current node in the data
  flow graph. It returns 0 for an instruction that does not have any previous
  instructions.
---

# Instruction.backward\_df()

Query

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().exec(1,16)
  # return the list of previous instructions of the current instruction
  return instructions[0].backward_df() 
```

Output

```json
{
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "function transferOwnership(address newOwner) public virtual onlyOwner {\n        require(newOwner != address(0),\"Ownable: new owner is the zero address\");\n        _setOwner(newOwner);\n    }", 
    "sol_instruction": "require(newOwner != address(0),\"Ownable: new owner is the zero address\")"
}
```
