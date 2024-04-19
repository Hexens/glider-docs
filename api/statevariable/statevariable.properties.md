---
description: Returns the list of the state variable's properties.
---

# StateVariable.properties()

`properties() → List[StateVariableProp]`

**Query Example**

```python
from glider import *
def query():
	state_vars = StateVariables().exec(3)
	for state_var in state_vars:
		print(state_var.name())
		print(state_var.properties())
	return []
```

**Output**

```solidity
"root":{1 item
"print_output":[6 items
0:string"_owner"
1:string"['private']"
2:string"_decimals"
3:string"['private', 'constant']"
4:string"uniswapV2Router"
5:string"['private']"
]
}
```
