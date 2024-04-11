---
description: >-
  Returns Functions object for the functions that are called from the current
  node corresponding function.
---

# CallNode.callee\_functions()

```python
from glider import *

# task: find a function that has `burn*` call and print all the functions that is called from it

def query():
  data = []
  instructions = Instructions().with_called_function_name_prefix('burn').exec(10)
  for instruction in instructions:
    if len(data) > 0:
      break # demo first result only
    functionContainsBurn = instruction.get_parent() #api.functions.Function (*)
    contract = functionContainsBurn.get_contract() #api.contracts.Contract
    call_graph = contract.call_graph() #api.call_graph.CallGraph 
    nodes = call_graph.nodes() #Dict[str, CallNode]
    for id in nodes:
      if(id != functionContainsBurn.db_id):
        continue
      callee_functions = nodes[id].callee_functions #api.functions.Functions
      callees = callee_functions().exec() #List[Function]
      if len(callees) > 0:
        print(functionContainsBurn.source_code())
        for callee in callees:
          print("callee: " + callee.name())
        data.append(instruction)
  return data
```

Output:

```json
{
  "print_output": [
    "function _burnRusdHeld() internal {\n        rusd().burn(rusdBalance());\n    }",
    "callee: rusd",
    "callee: rusdBalance",
    "callee: burn",
    "callee: burn"
  ]
}
```
