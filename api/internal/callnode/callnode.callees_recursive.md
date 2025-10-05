---
description: >-
  Returns all nodes corresponding the callees of the corresponding callable with
  the callees of those callables etc.
---

# CallNode.callees\_recursive()

`callees_recursive() →` [`APISet`](../../iterables/apiset.md)`[`[`CallNode`](./)`]`

## Query Example

```python
from glider import *


def query():
    contracts = Contracts().exec(1,3)
    contract = contracts[0]

    call_nodes = contract.call_graph().all_nodes()
    call_node = call_nodes[32]

    print(f"Call node callable name: {call_node.callable_name()}")

    for callee in call_node.callees_recursive():
        print(f"Extended callee callable name: {callee.callable_name()}")

    return contracts
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 6.09.15 PM.png" alt=""><figcaption></figcaption></figure>
