---
description: Returns corresponding callable name.
---

# CallNode.callable\_name()

`callable_name() → str`

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1)
    contract = contracts[0]

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
      "_msgSender()",
      "_msgData()"
    ]
  }
]
```
