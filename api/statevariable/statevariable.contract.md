---
description: Returns state variable's parent contract if it exists.
---

# StateVariable.contract()

`contract() →` [`Contract`](../contract/) `| NoneObject`

The function returns the Contract object (if exists, otherwise NoneObject) of the contract where the state variable is declared.

**Query Example**

```python
from glider import *
def query():
	state_vars = StateVariables().exec(1)
	print(state_vars[0].name())
	return [state_vars[0].contract()]
```

**Output**

```solidity
"root":{2 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Ownable"
},
"root":{1 item
"print_output":[1 item
    0:string"_owner"
    ]
}
```
