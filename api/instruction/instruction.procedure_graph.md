# Instruction.procedure\_graph

Returns the instruction's parent function's procedure graph.

Query

```python
from glider import *
def query():
  node_instruction = []
  instructions = Instructions().exec(1)
  #get the procedure_graph object 
  procedure_graph = instructions[0].procedure_graph
  #The procdure_graph has a property called all_nodes 
  #which returns a list of all the nodes in the graph
  all_nodes = procedure_graph.all_nodes
  #return the instruction corresponding to the first node
  node_instruction.append(all_nodes[0].instruction)
  return node_instruction

```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context",
  "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }",
  "sol_instruction": "{\n        return msg.sender;\n    }"
}
```
