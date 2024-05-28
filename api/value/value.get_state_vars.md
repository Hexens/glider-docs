---
description: >-
  Returns a list of Var objects of current value whose corresponding object is a
  StateVariable.
---

# Value.get\_state\_vars()

`get_state_vars() -> List[`[`Var`](var/)`]`

The function returns all the state variables used (read/written) inside the Value.

## Example

```python
from glider import *

def query():
	# lets find some functions that read/write state vars
	functions = Functions()\
		.with_one_property([MethodProp.HAS_STATE_VARIABLES_READ, MethodProp.HAS_STATE_VARIABLES_WRITTEN])\
		.exec(2)
        
	for function in functions:
		for instruction in function.instructions().exec():
			for operand in instruction.get_operands() + instruction.get_dest():
				state_vars = operand.get_state_vars()
				if len(state_vars)>0:
					print([x.expression for x in state_vars])
	return functions
```

## Example Output

```solidity
"root":{3 items
"contract":string"0xae690cf07c85bfb2de29ab32080c0ea182ae82b5"
"contract_name":string"REBITCOIN"
"sol_function":solidity
function REBITCOIN()
     //this is the token contract name, change to liking//

     {
        owner = msg.sender;
        balances[owner] = _totalSupply;
     }
}
"root":{3 items
"contract":string"0xae690cf07c85bfb2de29ab32080c0ea182ae82b5"
"contract_name":string"REBITCOIN"
"sol_function":solidity
function totalSupply() constant returns (uint256 l_totalSupply) 
     {
        l_totalSupply = _totalSupply;
     }
}
"root":{1 item
"print_output":[4 items
0:string"['owner']"
1:string"['_totalSupply']"
2:string"['balances', 'owner']"
3:string"['_totalSupply']"
]
}
```
