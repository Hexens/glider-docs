# CallGraph.with\_name\_not()

**`with_name_not`**`(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) → List[`[`CallNode`](../callnode/)`]`

Returns a list of call nodes whose corresponding function doesn't have the specified name.

## Return type

`→ List[`[`CallNode`](../callnode/)`]`

<pre class="language-python"><code class="lang-python">from glider import *

def query():
<strong>  # Fetch the first contract
</strong>  contracts = Contracts().exec(1)
  
  # Get call nodes of functions whose name is not "_msgSender"
  call_nodes = contracts[0].call_graph().with_name_not("_msgSender")
  for node in call_nodes:
    print(node.function_name())
  return []
</code></pre>

Output:

```json
{
  "print_output": [
    "_msgData"
  ]
}
```
