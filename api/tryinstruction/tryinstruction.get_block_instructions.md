# TryInstruction.get\_block\_instructions()

## Description

The method returns a list of instruction in a `try` block.

## Return type

List\[[Instruction](../instruction/)]

## Example query

```python
from glider import *


def query():
    instructions = (
        Contracts()
        .mains()
        .functions()
        .with_one_property([MethodProp.EXTERNAL, MethodProp.PUBLIC])
        .instructions()
        .try_instructions()
        .exec(1, 10)
    )

    result = []
    for instruction in instructions:
        block_instructions = instruction.get_block_instructions()

        for bi in block_instructions:
            result.append(bi)

    return result
```

## Example output

```solidity
{
    "contract": "0x3b5A61227434AFD62ADBF133074Fb857D648cE69"
    "contract_name": "TokenaFactory"
    "sol_function":
	function checkValidLpAddress(address adr) public view returns (bool) {
		require(adr != address(0),"lp token address 0x0");
		try IUniswapV2Pair(adr).factory() returns (address factory) {
			return factory == dexFactory;
		} catch {
			return false;
		}	
	}
    "sol_instruction":
	return factory == dexFactory
}
```
