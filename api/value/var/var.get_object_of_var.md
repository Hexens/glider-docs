---
description: Returns corresponding object of the variable.
---

# Var.get\_object\_of\_var()

The function returns the appropriate object for the Var, such as: [LocalVariable](../../localvariable/), [StateVariable](../../statevariable/), GlobalVariable, [Argument](../../argument/).

It is essential to understand that Var represents not just a variable in general but a specific "placement" of that variable in the code while the classes like LocalVariabl or StateVariable etc. represent the variable itself.

It is easy to see in an example:

```solidity
function addBots(address[] memory bots) public onlyOwner() {
        for (uint i = 0; i < bots.length; i++) {
            if (bots[i] != uniswapV2Pair && bots[i] != address(uniswapV2Router)) {
                isBot[bots[i]] = true;
            }
        }
    }
```

Here the `bots`argument is used in different instructions, and each usage of the bots will be represented by a different Var, while the Argument object that can be retrieved using the get\_object\_of\_var() function will represent the `bots` in general as an argument.

## Example

```python
from glider import *

def query():
	functions = Functions()\
		.with_one_property([MethodProp.HAS_STATE_VARIABLES_WRITTEN])\
		.exec(50,50)
	
	for function in functions:
		for instruction in function.instructions().exec():
			for operand in instruction.get_operands():
				vars = operand.get_local_vars()
				if len(vars)>0:
					for point in vars[0].forward_df():
						print("Var: "+vars[0].expression)
						local_var = vars[0].get_object_of_var()
						# lets use something specific to LocalVariable
						print(local_var.type)
						return [instruction]
	return []

```

## Example Output&#x20;

```solidity
"root":{4 items
"contract":string"0xc19163d5937a170029ac6858836e57476c74cddd"
"contract_name":string"KadyrovInu"
"sol_function":solidity
function addBots(address[] memory bots) public onlyOwner() {
        for (uint i = 0; i < bots.length; i++) {
            if (bots[i] != uniswapV2Pair && bots[i] != address(uniswapV2Router)) {
                isBot[bots[i]] = true;
            }
        }
    }
"sol_instruction":solidity
i++
}
"root":{1 item
"print_output":[2 items
0:string"Var: i"
1:string"uint256"
]
}
```
