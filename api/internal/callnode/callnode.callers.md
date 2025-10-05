---
description: >-
  Returns a list of CallNodes whose corresponding functions call the current
  node's corresponding function.
---

# CallNode.callers()

`callers() →` [`APIList`](../../iterables/apilist.md)`[`[`CallNode`](./)`]`

## Query Example

```python
from glider import *


def query():
    data = []
    instructions = Instructions().with_callee_name_prefix('burn').exec(10)

    for instruction in instructions:
        if len(data) > 0:
            break # demo first result only
        functionContainsBurn = instruction.get_parent() #api.functions.Function (*)
        contract = functionContainsBurn.get_contract() #api.contracts.Contract
        call_graph = contract.call_graph() #api.call_graph.CallGraph 
        nodes = call_graph.nodes() #Dict[str, CallNode]
        for id in nodes:
            if(id != functionContainsBurn.db_id):
                continue
        callers = nodes[id].callers() # APIList[CallNode]
        if len(callers) > 0:
            print(functionContainsBurn.source_code())
            for caller in callers:
                print("caller: " + caller.callable_name())
            data.append(instruction)

    return data
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 6.09.37 PM.png" alt=""><figcaption></figcaption></figure>
