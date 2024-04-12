---
description: Returns the list of all pragmas of the contract.
---

# Contract.pragmas()

## Return type

List\[Tuple\[str, str]]

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 100)
  
  result = []
  for contract in contracts:
    pragmas = contract.pragmas()
    result.append(pragmas[0])

  return result
```

## Example output

```json
"root":[2 items
0:string"RollBot.sol"
1:[7 items
0:[4 items
0:string"solidity"
1:string"^"
2:string"0.8"
3:string".0"
]
1:[4 items
0:string"solidity"
1:string"^"
2:string"0.8"
3:string".0"
]
2:[4 items
0:string"solidity"
1:string"^"
2:string"0.8"
3:string".0"
]
```
