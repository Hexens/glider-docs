---
description: >-
  Returns Modifiers object for the modifiers that call the current node
  corresponding callable.
---

# CallNode.caller\_modifiers()

`caller_modifiers() →` [`Modifiers`](../../callables/modifiers/)

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1,3)
    contract = contracts[0]

    call_nodes = contract.call_graph().all_nodes()
    call_node = call_nodes[43]

    print(f"Call node function name: {call_node.callable_name()}")

    for modifier in call_node.caller_modifiers().exec():
        print(f"Caller modifier name {modifier.name}")

    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "Call node function name: _msgSender",
      "Caller modifier name onlyOwner"
    ]
  }
]
```
