---
description: Adds a filter to get state variables that have all given properties.
---

# StateVariables.with\_all\_properties()

`with_all_properties(properties: List[`[`StateVariableProp`](statevariableprop/)`]) →` [`StateVariables`](./)

**Query Example**

```python
from glider import *
def query():
	state_vars = StateVariables().with_all_properties([StateVariableProp.IMMUTABLE, StateVariableProp.PUBLIC]).exec(1)
	for state_var in state_vars:
		print(state_var.name())
		print(state_var.properties())
	return []
```

**Output**

```solidity
"root":{1 item
"print_output":[2 items
0:string"uniswapV2Router"
1:string"['public', 'immutable']"
]
}
```
