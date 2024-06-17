# CallGraph.with\_name()

**`with_name`**`(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) → List[`[`CallNode`](../callnode/)`]`

Returns a list of call nodes whose corresponding function has the specified name.

## Return type

`→ List[`[`CallNode`](../callnode/)`]`

<pre class="language-python"><code class="lang-python">from glider import *

def query():
<strong>  # Fetch the first contract
</strong>  contracts = Contracts().exec(1)
  
  # Get call nodes of functions whose name is "_msgSender"
  call_nodes = contracts[0].call_graph().with_name("_msgSender")
  for node in call_nodes:
    print(node.callable_name())
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
