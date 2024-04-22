---
description: >-
  Returns a list of CallNodes whose corresponding functions call the current
  node's corresponding function.
---

# CallNode.callers()

```python
from glider import *

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
      callers = nodes[id].callers() #List[CallNode]
      if len(callers) > 0:
        print(functionContainsBurn.source_code())
        for caller in callers:
          print("caller: " + caller.function_name())
        data.append(instruction)
  return data
```

Output:

```json
{
  "print_output": [
    "function _beforeTokenTransfer(\n        address from,address to,uint256 amount\n    ) internal virtual override {\n        super._beforeTokenTransfer(from,to,amount);\n        \n        if (from == address(0) && to != address(0)) {\n            require(_erc20TokenAddress != address(0),\"_erc20TokenAddress must be defined\");\n            uint256 balanceOfAddress = IERC20(_erc20TokenAddress).balanceOf(to);\n            require(balanceOfAddress >= 1,\"user does not hold a token\");\n            ERC20Burnable(_erc20TokenAddress).burnFrom(to,1);\n        }\n    }",
    "caller: _mint",
    "caller: _burn",
    "caller: _transfer"
  ]
}
```
