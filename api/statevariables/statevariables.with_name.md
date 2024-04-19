---
description: Adds a filter to get state variables with the given name.
---

# StateVariables.with\_name()

`with_name(name: str, sensitivity: bool = True) →` [`StateVariables`](./)

**Query Example**

```python
from glider import *
def query():
	state_vars = StateVariables().with_name('balance', sensitivity=False).exec(2)
	for state_var in state_vars:
		print(state_var.name())
		print(state_var.properties())
	return []
```

**Output**

```solidity
"root":{1 item
"print_output":[4 items
0:string"balance"
1:string"['internal']"
2:string"BALANCE"
3:string"['constant', 'internal']"
]
}
```
