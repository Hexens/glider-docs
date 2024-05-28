---
description: >-
  Returns a list of Var objects of current value whose corresponding object is a
  GlobalVariable.
---

# Value.get\_global\_vars()

`get_global_vars() -> List[`[`Var`](var/)`]`

The function returns all the global variables, e.g. `msg.sender, msg.value, tx.origin, ...`, used inside the Value.

For the list of global variables, please refer to GlobalVariables.

## Example

```python
from glider import *

def query():
	# lets find _msgSender functions as there should be a msg.sender usage
	functions = Functions()\
		.with_name('_msgSender')\
		.exec(1)
	
	for function in functions:
		for instruction in function.instructions().exec():
			for operand in instruction.get_operands():
				global_vars = operand.get_global_vars()
				if len(global_vars)>0:
					print([x.expression for x in global_vars])
	return functions

```

## Example Output

```solidity
"root":{3 items
"contract":string"0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb"
"contract_name":string"Context"
"sol_function":solidity
function _msgSender() internal view virtual returns (address payable) {
        return msg.sender;
    }
}
"root":{1 item
"print_output":[1 item
0:string"['msg.sender']"
]
}
```
