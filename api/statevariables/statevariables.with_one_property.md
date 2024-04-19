---
description: >-
  Adds a filter to get state variables that at least have one of the given
  properties.
---

# StateVariables.with\_one\_property()

`with_one_property(properties: List[`[`StateVariableProp`](../statevariableprop/)`]) →` [`StateVariables`](./)

**Query Example**

```python
from glider import *
def query():
	state_vars = StateVariables().with_one_property([StateVariableProp.IMMUTABLE, StateVariableProp.PUBLIC]).exec(3)
	for state_var in state_vars:
		print(state_var.name())
		print(state_var.properties())
	return []
```

**Output**

```solidity
"root":{1 item
"print_output":[6 items
0:string"tradeOpen"
1:string"['public']"
2:string"name"
3:string"['public']"
4:string"symbol"
5:string"['public']"
]
}
```
