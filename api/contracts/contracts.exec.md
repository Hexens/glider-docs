---
description: Executes the formed query and returns the list of Contract objects.
---

# Contracts.exec()

Input:

```python
from glider import *

def query():
  contracts = Contracts().exec(2)

  return contracts
```

Output:

```python
"root":{2 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Context"
}
"root":{2 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Ownable"
}
```
