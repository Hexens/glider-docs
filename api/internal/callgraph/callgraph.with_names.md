---
description: >-
  Returns the list of call nodes whose corresponding function has the specified
  name.
---

# CallGraph.with\_names()

`with_names(`_`names: List[str],sensitivity: bool = True`_`) →` [`APIList`](../../iterables/apilist.md)`[`[`CallNode`](../callnode/)`]`&#x20;

## Query Example

```python
from glider import *


def query():
    # Fetch the first contract
    contracts = Contracts().exec(1)
  
    # Get call nodes of functions ending with "Sender" 
    call_nodes = contracts[0].call_graph().with_names(["_msgSender", "_msgData"])
    for node in call_nodes:
        print(node.callable_name())

    return contracts
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 5.51.30 PM.png" alt=""><figcaption></figcaption></figure>
