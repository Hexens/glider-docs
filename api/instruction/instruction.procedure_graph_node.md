---
description: Returns corresponding node in procedure graph.
---

# Instruction.procedure\_graph\_node

Query

```python
from glider import *
def query():
  #fetch a list of instructions
  instructions = Instructions().exec(1,16)
  procedure_graph_node = instructions[0].procedure_graph_node
  #Return the instruction corresponding to the procedure_graph_node 
  return [procedure_graph_node.instruction]
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
