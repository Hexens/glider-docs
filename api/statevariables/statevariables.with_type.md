---
description: Adds a filter to get state variables that have the given type.
---

# StateVariables.with\_type()

`with_type(variable_type: str) →` [`StateVariables`](./)

**Query Example**

```python
from glider import *
def query():
	state_vars = StateVariables().with_type('mapping(address => bool)').exec(1)
	for state_var in state_vars:
		print(state_var.name())
		print(state_var.properties())
	return []
```

**Output**

```solidity
"root":{1 item
"print_output":[2 items
0:string"_isExcludedFromFee"
1:string"['private']"
]
}
```
