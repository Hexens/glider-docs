---
description: Returns the state variable's name.
---

# StateVariable.name()

`name() → str`

**Query Example**

```python
from glider import *
def query():
	state_vars = StateVariables().exec(3)
	for state_var in state_vars:
		print(state_var.name())
	return []
```

**Output**

```solidity
"root":{1 item
"print_output":[3 items
0:string"_owner"
1:string"_decimals"
2:string"uniswapV2Router"
]
}
```
