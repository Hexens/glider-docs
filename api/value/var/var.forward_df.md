---
description: >-
  Returns a list of all instructions following the current point in the current
  data flow graph
---

# Var.forward\_df()

`forward_df() -> List[`[`Instruction`](../../instruction/)`]`

The function works similarly to [Instruction.forward\_df()](../../instruction/instruction.forward\_df.md); the main difference is that in case of Instruction.forward\_df() the function will return forward-dataflow point for every point in the instruction, while Var.forward\_df() returns only those connected with the current Var.&#x20;

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
						# print(point.source_code())
						return vars[0].forward_df()
	return []

```

For the local variable (Var) `uint i=0;` in the function:

```solidity
function addBots(address[] memory bots) public onlyOwner() {
        for (uint i = 0; i < bots.length; i++) {
            if (bots[i] != uniswapV2Pair && bots[i] != address(uniswapV2Router)) {
                isBot[bots[i]] = true;
            }
        }
    }
```

The output will be:

## Example Output

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
bots[i] != uniswapV2Pair && bots[i] != address(uniswapV2Router)
}
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
i < bots.length
}
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
isBot[bots[i]] = true
}

```
