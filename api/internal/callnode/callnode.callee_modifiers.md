---
description: >-
  Returns Modifiers object for the modifiers that are called from the current
  node corresponding callable.
---

# CallNode.callee\_modifiers()

`callee_modifiers() →` [`Modifiers`](../../callables/modifiers/)

## Query Example

```python
from glider import *


def query():
    contracts = Contracts().exec(10,1)
    contract = contracts[0]

    call_nodes = contract.call_graph().all_nodes()
    call_node = call_nodes[31]
    call_node_name = call_node.callable_name()
    
    for modifier in call_node.callee_modifiers().exec():
        print(f"Function name: {call_node_name} | Callee modifier name: {modifier.name}")

    return contracts
```

## Output Example

Output below represents printed output from the caller's source code:

```json
[
  {
    "print_output": [
      "Function name: renounceOwnership | Callee modifier name: onlyOwner"
    ]
  }
]
```

