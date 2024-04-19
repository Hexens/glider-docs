---
description: >-
  Returns true if the visibility of the state variable is private, otherwise
  returns false.
---

# StateVariable.is\_private()

`is_private() → bool`

**Query Example**

```python
from glider import *
def query():
  state_vars = StateVariables().exec(100)
  for state_var in state_vars:
    if state_var.is_private():
      print(state_var.name())
      return [state_var.contract()]
  return []
```

**Output**

```solidity
"root":{2 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Ownable"
}
"root":{1 item
"print_output":[1 item
0:string"_owner"
]
}
```
