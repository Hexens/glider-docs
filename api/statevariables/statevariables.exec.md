---
description: Executes the formed query and returns a list of StateVariable objects.
---

# StateVariables.exec()

`exec(limit_count: int = 0, offset_count: int = 0) → List[`[`StateVariable`](../statevariable/)`]`

**Query Example**

```python
from glider import *
def query():
	state_vars = StateVariables().exec(3,3)
	for state_var in state_vars:
		print(state_var.name())
		print(state_var.properties())
	return []
```

**Output**

```solidity
"root":{1 item
"print_output":[6 items
0:string"_isExcludedFromFee"
1:string"['private']"
2:string"_tTotal"
3:string"['private', 'constant']"
4:string"_initialBuyTax"
5:string"['private']"
]
}
```
