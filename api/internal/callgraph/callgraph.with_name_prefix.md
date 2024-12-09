---
description: >-
  Returns the list of call nodes whose corresponding function name has the
  specified suffix.
---

# CallGraph.with\_name\_prefix()

`with_name_prefix(`_`suffix: str`_`,`` `_`sensitivity: bool = True`_`) →` [`APIList`](../../iterables/apilist.md)`[`[`CallNode`](../callnode/)`]`

## Query Example

<pre class="language-python"><code class="lang-python">from glider import *

def query():
<strong>    # Fetch the first contract
</strong><strong>    contracts = Contracts().exec(1)
</strong>  
    # Get call nodes of functions starting with "_msgSend" 
    call_nodes = contracts[0].call_graph().with_name_prefix("_msgSend")
    for node in call_nodes:
        print(node.callable_name())
    
    return []
</code></pre>

## Example Output

```json
{
  "print_output": [
    "_msgSender"
  ]
}
```
