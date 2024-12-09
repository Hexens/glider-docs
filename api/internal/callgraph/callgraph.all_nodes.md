---
description: Returns the list of all call nodes.
---

# CallGraph.all\_nodes()

`all_nodes() →` [`APIList`](../../iterables/apilist.md)`[`[`CallNode`](../callnode/)`]`

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1)
    contract = contracts[0]

    for func in contract.functions().exec():
        call_nodes = contract.call_graph().all_nodes()
        for call_node in call_nodes:
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
