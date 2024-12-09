---
description: >-
  Returns the list of call nodes whose corresponding function name has the
  specified suffix.
---

# CallGraph.with\_name\_suffix()

`with_name_suffix(`_`suffix: str`_`,`` `_`sensitivity: bool = True`_`) →` [`APIList`](../../iterables/apilist.md)`[`[`CallNode`](../callnode/)`]`

## Query Example

```python
from glider import *

def query():
    # Fetch the first contract
    contracts = Contracts().exec(1)
  
    # Get call nodes of functions ending with "Sender" 
    call_nodes = contracts[0].call_graph().with_name_suffix("Sender")
    for node in call_nodes:
        print(node.callable_name())
    return []
```

## Output Example

```json
{
  "print_output": [
    "_msgSender"
  ]
}
```
