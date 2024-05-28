---
description: Returns a list of all Var objects of current value.
---

# Value.get\_vars()

`get_vars() -> List[`[`Var`](var/)`]`

The function returns all the Var's used (read/written) inside the Value.&#x20;

It returns Vars for state, local and global variables and arguments, basically combining the calls to get\_state\_vars, get\_local\_vars, get\_global\_vars and get\_arg\_vars.

## Example

```python
from glider import *

def query():
	functions = Functions()\
		.with_name('bridgeTokens')\
		.exec(1)
	
	for function in functions:
		for instruction in function.instructions().exec():
			print(instruction.source_code())
			for operand in instruction.get_operands():
				vars = operand.get_vars()
				if len(vars)>0:
					print([x.expression for x in vars])
	return functions

```

## Example Output

```solidity
"root":{3 items
"contract":string"0xeF833c44d32c1D7a5526910f1E2C21467395b2A2"
"contract_name":string"L1Vault"
"sol_function":solidity
function bridgeTokens(
        uint256 destinationNetwork,address destination,address token,uint256 amount,bytes calldata _data
    ) external onlyOwner validAddress(destination) validAmount(amount) {
        composableHolding.approve(address(bridgeAggregator),token,amount);
        bridgeAggregator.bridgeTokens(
            destinationNetwork,destination,token,amount,_data
        );
    }
}
"root":{1 item
"print_output":[10 items
0:string"{
        composableHolding.approve(address(bridgeAggregator),token,amount);
        bridgeAggregator.bridgeTokens(
            destinationNetwork,destination,token,amount,_data
        );
    }"
1:string"composableHolding.approve(address(bridgeAggregator),token,amount)"
2:string"['bridgeAggregator', 'token', 'amount']"
3:string"bridgeAggregator.bridgeTokens(
            destinationNetwork,destination,token,amount,_data
        )"
4:string"['destinationNetwork', 'destination', 'token', 'amount', '_data']"
5:string"onlyOwner"
6:string"validAddress(destination)"
7:string"['destination']"
8:string"validAmount(amount)"
9:string"['amount']"
]
}
```
