---
description: Returns a list of Contract objects.
---

# Contracts.contracts

Input:

```python
from glider import *

def query():
  contracts = Contracts().exec(1)

  return contracts
```

Output:

```python
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context"
}
```
