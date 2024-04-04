# CallGraph.name\_prefix()

**`name_prefix`**`(`_`suffix: str`_`,`` `_`sensitivity: bool = True`_`) → List[`[`CallNode`](../callnode/)`]`

Returns a list of [CallNode](../callnode/) objects whose corresponding function name has the specified prefix.

## Return type

`→ List[`[`CallNode`](../callnode/)`]`

<pre class="language-python"><code class="lang-python">from glider import *

def query():
<strong>  # Fetch the first contract
</strong>  contracts = Contracts().exec(1)
  
  # Get call nodes of functions starting with "_msgSend" 
  call_nodes = contracts[0].call_graph().name_prefix("_msgSend")
  for node in call_nodes:
    print(node.function_name())
  return []
</code></pre>

Output:

```json
{
  "print_output": [
    "_msgSender"
  ]
}
```
