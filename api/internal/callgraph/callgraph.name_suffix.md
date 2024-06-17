# CallGraph.name\_suffix()

**`name_suffix`**`(`_`suffix: str`_`,`` `_`sensitivity: bool = True`_`) → List[`[`CallNode`](../callnode/)`]`

Returns a list of [CallNode](../callnode/) objects whose corresponding function name has the specified suffix.

## Return type

`→ List[`[`CallNode`](../callnode/)`]`

```python
from glider import *

def query():
  # Fetch the first contract
  contracts = Contracts().exec(1)
  
  # Get call nodes of functions ending with "Sender" 
  call_nodes = contracts[0].call_graph().name_suffix("Sender")
  for node in call_nodes:
    print(node.callable_name())
  return []
```

Output:

```json
{
  "print_output": [
    "_msgSender"
  ]
}
```
