---
description: >-
  Returns all nodes corresponding the callers of the corresponding callable with
  the callers of those callables etc.
---

# CallNode.callers\_recursive()

`callers_recursive() →` [`APISet`](../../iterables/apiset.md)`[`[`CallNode`](./)`]`

## Query Example

```python
from glider import *


def query():
    contracts = Contracts().exec(1,3)
    contract = contracts[0]

    call_nodes = contract.call_graph().all_nodes()
    call_node = call_nodes[13]
    
    print(f"Call node callable name: {call_node.callable_name()}")
    
    for callee in call_node.callers_recursive():
        print(f"Extended caller callable name: {callee.callable_name()}")
 
    return contracts
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 6.08.48 PM.png" alt=""><figcaption></figcaption></figure>
