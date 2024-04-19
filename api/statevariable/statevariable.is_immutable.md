---
description: Returns true if the state variable is immutable, otherwise returns false.
---

# StateVariable.is\_immutable()

`is_immutable() → bool`

**Query Example**

```python
from glider import *
def query():
  state_vars = StateVariables().exec(100)
  for state_var in state_vars:
    if state_var.is_immutable():
      print(state_var.name())
      return [state_var.contract()]
  return []
```

**Output**

```solidity
"root":{2 items
"contract":string"0x5e6b2027f794a069bfa5e80195e22544d40ae600"
"contract_name":string"NATEHALLINAN"
},
"root":{1 item
"print_output":[1 item
0:string"uniswapV2Router"
]
}
```
