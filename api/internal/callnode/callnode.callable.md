---
description: Returns corresponding callable.
---

# CallNode.callable()

`callable() →` [`Callable`](../../callable/)

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1)
    contract = contracts[0]

    call_nodes = contract.call_graph().all_nodes()
    for call_node in call_nodes:
        callable = call_node.callable()
        print(callable.signature())

    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "_msgSender()",
      "_msgData()"
    ]
  }
]
```
