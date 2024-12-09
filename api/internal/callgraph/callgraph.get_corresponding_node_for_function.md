---
description: Returns the node which represents the given function.
---

# CallGraph.get\_corresponding\_node\_for\_function()

`get_corresponding_node_for_function(function:` [`Callable`](../../callable/)`) →` [`CallNode`](../callnode/)

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1)
    contract = contracts[0]

    for func in contract.functions().exec():
        call_node = contract.call_graph().get_corresponding_node_for_function(func)
        print(call_node.callable_name())

    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "_msgSender",
      "_msgData"
    ]
  }
]
```
