---
description: Returns corresponding function name.
---

# CallNode.function\_name()

```python
from glider import *

# find a contract with name UnistakeToken and print all the functions inside
def query():
  contracts = Contracts().name_regex("UnistakeToken").exec(5)
  for contract in contracts:
    call_graph = contract.call_graph() #api.call_graph.CallGraph instance 
    nodes = call_graph.nodes() #api.call_graph.CallNode instance
    for id in nodes:
      print(nodes[id].function_name())
  return contracts
```

Output:

```json
{
  "print_output": [
    "burn",
    "burnFrom",
    "constructor",
    "name",
    "symbol",
    "decimals",
    "totalSupply",
    "balanceOf",
    "transfer",
    "allowance",
    "approve",
    "transferFrom",
    "increaseAllowance",
    "decreaseAllowance",
    "_transfer",
    "_mint",
    "_burn",
    "_approve",
    "_spendAllowance",
    "_beforeTokenTransfer",
    "_afterTokenTransfer",
    "_msgSender",
    "_msgData",
    "constructor"
  ]
}
```

