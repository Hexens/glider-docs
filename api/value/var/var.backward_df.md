---
description: >-
  Returns a list of all previous instructions/arguments of the current point in
  the data flow graph.
---

# Var.backward\_df()

`backward_df() -> List[Point]`

The function works similarly to [Instruction.backward\_df()](../../instruction/instruction.backward\_df.md); the main difference is that in case of Instruction.backward\_df() the function will return backward dataflow point for every point in the instruction, while Var.backward\_df() returns only those connected with the current Var.&#x20;

Like all other dataflow (DF) functions, it returns a list/set of Points, which can be instructions or "points" in the code, such as arguments, variables, etc.

## Example

```python
from glider import *

def query():
	functions = Functions()\
		.with_name('_transfer')\
		.exec(1)
	
	for function in functions:
		for instruction in function.instructions().exec():
			# print(instruction.source_code())
			for operand in instruction.get_operands():
				vars = operand.get_vars()
				if len(vars)>0:
					print("Var: "+vars[0].expression)
					for point in vars[0].backward_df():
						print(point.source_code())
					return functions
	

```

## Example Output

```solidity
root":{3 items
"contract":string"0x31a13db822593aafef324ef2655e31b05b2577c0"
"contract_name":string"ERC20"
"sol_function":solidity
function _transfer(address sender,address recipient,uint256 amount) internal virtual {
        require(sender != address(0),"ERC20: transfer from the zero address");
        require(recipient != address(0),"ERC20: transfer to the zero address");
 
        uint256 senderBalance = _balances[sender];
        require(senderBalance >= amount,"ERC20: transfer amount exceeds balance");
        _balances[sender] = senderBalance - amount;
        _balances[recipient] += amount;
 
        emit Transfer(sender,recipient,amount);
    }
}
"root":{1 item
"print_output":[3 items
0:string"Var: sender"
1:string"require(sender != address(0),"ERC20: transfer from the zero address")"
2:string"address sender"
]
}
```
