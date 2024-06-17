# CallGraph.nodes()

**`nodes`**`() → Dict[str,` [`CallNode`](../callnode/)`]`

Returns the map of all call nodes. The key of the map is the id of a node.

```python
from glider import *

def query():
  # Query first contract
  contracts = Contracts().exec(1)
  
  # Get all call nodes from the contract's call graph
  call_nodes = contracts[0].call_graph().nodes()
  
  # print all call nodes' corresponding function names
  for node_id in call_nodes:
    print(call_nodes[node_id].callable_name())
  return []
```

Output:

```json
{
    "print_output": [
        string"REBITCOIN",
        string"totalSupply",
        string"totalBurned",
        string"balanceOf",
        string"transfer",
        string"transferFrom",
        string"approve",
        string"allowance",
        string"burn",
        string"burnFrom",
        string"onlyOwner"
    ]
}
```

