---
description: Returns whether the node represents a modifier.
---

# CallNode.is\_modifier

_`property`_` ``is_function : bool`

## Query Example

```python
from glider import *


def query():
    contracts = Contracts().exec(1,3)
    contract = contracts[0]

    call_nodes = contract.call_graph().all_nodes()
    call_node = call_nodes[55]
    
    print(f"Is call node {call_node.callable_name()} a modifier: {call_node.is_modifier}")
  
    return contracts
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 6.07.36 PM.png" alt=""><figcaption></figcaption></figure>
