---
description: >-
  Adds a filter to get contracts that don't have any function with the given
  name.
---

# Contracts.with\_function\_name\_not()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_function_name_not('transfer').exec(5)

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
"root":{2 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"IERC165"
}
"root":{2 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"ERC165"
}
"root":{2 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"IERC721"
}
```
