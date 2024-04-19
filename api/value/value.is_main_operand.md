---
description: Returns true is the value represents the main operand
---

# Value.is\_main\_operand()

`is_main_operand() → bool`

**Query Example**

```python
from glider import *
def query():
	instructions = Instructions().exec(1,1)
	operands = instructions[0].get_operands()
	for operand in operands:
		if operand.is_main_operand():
			print(operand.expression)
	return instructions
```

**Output**

```solidity
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Context"
"sol_function":solidity
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
"sol_instruction":solidity
return msg.sender
}
"root":{1 item
"print_output":[1 item
0:string"msg.sender"
]
}
```
