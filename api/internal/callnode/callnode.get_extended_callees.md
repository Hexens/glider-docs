---
description: >-
  Returns all nodes corresponding the callees of the corresponding callable with
  the callees of those callables etc.
---

# CallNode.get\_extended\_callees()

`get_extended_callees() →` [`APISet`](../../iterables/apiset.md)`[`[`CallNode`](./)`]`

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1,3)
    contract = contracts[0]

    call_nodes = contract.call_graph().all_nodes()
    call_node = call_nodes[32]

    print(f"Call node callable name: {call_node.callable_name()}")

    for callee in call_node.get_extended_callees():
        print(f"Extended callee callable name: {callee.callable_name()}")

    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "Call node callable name: transferOwnership",
      "Extended callee callable name: owner",
      "Extended callee callable name: _msgSender",
      "Extended callee callable name: onlyOwner"
    ]
  }
]
```
