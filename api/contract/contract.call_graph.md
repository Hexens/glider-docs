# Contract.call\_graph()

## Description

Returns call graph of the contract.

## Return type

[CallGraph](../callgraph/)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(50, 50)
  
  names = []
  for contract in contracts:
    call_graph = contract.call_graph()

    nodes = call_graph.name_prefix("min")

    for node in nodes:
      names.append(node.function_name())

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "mint",
    "mint",
    "minVotingPeriod",
    "mint"
  ]
}
```
