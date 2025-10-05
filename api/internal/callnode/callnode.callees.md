---
description: >-
  Returns a list of CallNode whose corresponding functions are called from the
  current CallNode corresponding function.
---

# CallNode.callees()

`callees() →` [`APIList`](../../iterables/apilist.md)`[`[`CallNode`](./)`]`

## Query Example

```python
from glider import *


def query():
  data = []
  instructions = Instructions().with_callee_name_prefix('burn').exec(10)
  
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
      callees = nodes[id].callees() #List[CallNode]
    
      if len(callees) > 0:
        print(functionContainsBurn.source_code())
        for callee in callees:
          print("callee: " + callee.callable_name())
        data.append(instruction)
        
  return data
```

## Example Output

Output below represents printed output from the caller's source code:

```json
{
  "print_output": [
    "function _burnRusdHeld() internal {\n        rusd().burn(rusdBalance());\n    }",
    "callee: rusd",
    "callee: rusdBalance"
  ]
}
```
