---
description: >-
  Returns true if the visibility of the state variable is public, otherwise
  returns false.
---

# StateVariable.is\_public()

`is_public() → bool`

**Query Example**

```python
from glider import *
def query():
  state_vars = StateVariables().exec(100)
  for state_var in state_vars:
    if state_var.is_public():
      print(state_var.name())
      return [state_var.contract()]
  return []
```

**Output**

```solidity
"root":{2 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Token"
},
"root":{1 item
"print_output":[1 item
0:string"tradeOpen"
]
}
```
