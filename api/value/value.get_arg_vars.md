---
description: >-
  Returns a list of Var objects of current value whose corresponding object is
  an argument variable.
---

# Value.get\_arg\_vars()

`get_arg_vars() -> List[`[`Var`](var/)`]`

The function returns all the arguments' vars used inside the Value.

## Example

```python
from glider import *

def query():
	# lets get some functions with exactly 3 arguments
	functions = Functions()\
		.with_arg_count(3)\
		.exec(2,20)
	
	for function in functions:
		for instruction in function.instructions().exec():
			for operand in instruction.get_operands():
				arg_vars = operand.get_arg_vars()
				if len(arg_vars)>0:
					print([x.expression for x in arg_vars])
	return functions

```

## Example Output

```solidity
"root":{3 items
"contract":string"0xe5fA13058EdE558a2bFA675043f175148858A5F6"
"contract_name":string"SafeMath"
"sol_function":solidity
function sub(uint256 a,uint256 b,string memory errorMessage) internal pure returns (uint256) {
        require(b <= a,errorMessage);
        uint256 c = a - b;
 
        return c;
    }
}
"root":{3 items
"contract":string"0xe5fA13058EdE558a2bFA675043f175148858A5F6"
"contract_name":string"SafeMath"
"sol_function":solidity
function div(uint256 a,uint256 b,string memory errorMessage) internal pure returns (uint256) {
        require(b > 0,errorMessage);
        uint256 c = a / b;
        
 
        return c;
    }
}
"root":{1 item
"print_output":[6 items
0:string"['b', 'a', 'errorMessage']"
1:string"['a']"
2:string"['b']"
3:string"['b', 'errorMessage']"
4:string"['a']"
5:string"['b']"
]
}
```
