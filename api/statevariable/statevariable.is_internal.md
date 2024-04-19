---
description: >-
  Returns true if the visibility of the state variable is internal, otherwise
  returns false.
---

# StateVariable.is\_internal()

`is_internal() → bool`

**Query Example**

```python
from glider import *
def query():
  state_vars = StateVariables().exec(100)
  for state_var in state_vars:
    if state_var.is_internal():
      print(state_var.name())
      return [state_var.contract()]
  return []
```

**Output**

```solidity
"root":{2 items
"contract":string"0x23297ee054e8f600af482013ddbe856b7178a7d3"
"contract_name":string"LibBytesRichErrors"
},
"root":{1 item
"print_output":[1 item
0:string"INVALID_BYTE_OPERATION_ERROR_SELECTOR"
]
}
```
