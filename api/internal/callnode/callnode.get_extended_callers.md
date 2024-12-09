---
description: >-
  Returns all nodes corresponding the callers of the corresponding callable with
  the callers of those callables etc.
---

# CallNode.get\_extended\_callers()

`get_extended_callers() →` [`APISet`](../../iterables/apiset.md)`[`[`CallNode`](./)`]`

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1,3)
    contract = contracts[0]

    call_nodes = contract.call_graph().all_nodes()
    call_node = call_nodes[13]
    
    print(f"Call node callable name: {call_node.callable_name()}")
    
    for callee in call_node.get_extended_callers():
        print(f"Extended caller callable name: {callee.callable_name()}")
 
    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "Call node callable name: transferAndCall",
      "Extended caller callable name: create_random_pizza",
      "Extended caller callable name: requestRandomness",
      "Extended caller callable name: requestRandomness"
    ]
  }
]
```
