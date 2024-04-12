# IfInstruction.first\_true\_instruction()

`first_true_instruction() →` [`Instruction`](../instruction/)

The function returns the first instruction for the true-case scenario of the if-statement

## Example

for the function:

```solidity
function mul(uint256 a,uint256 b) internal pure returns (uint256) {
    
    if (a == 0) {
      return 0;
    }
 
    uint256 c = a * b;
    require(c / a == b,"SafeMath: multiplication overflow");
 
    return c;
  }
```

The query (exec numbers are tuned here to match that exact if-statement)

```python
from glider import *

def query():
  instructionlist = Instructions().if_instructions().exec(1)
  
  first_true = instructionlist[0].first_true_instruction()

  return [first_true]
```

## Output

```solidity
"root":{4 items
"contract":string"0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb"
"contract_name":string"SafeMath_Chainlink"
"sol_function":solidity
function mul(uint256 a,uint256 b) internal pure returns (uint256) {
    
    
    
    if (a == 0) {
      return 0;
    }
 
    uint256 c = a * b;
    require(c / a == b,"SafeMath: multiplication overflow");
 
    return c;
  }
"sol_instruction":solidity
return 0
}
```



Interesting to note about the difference in this example and the [first\_false\_instruction()](ifinstruction.first\_false\_instruction.md) example, is that in the case of this function and this exact if-statement&#x20;

```solidity
    if (a == 0) {
      return 0;
    }
```

The [next\_instruction()](../instruction/instruction.next\_instruction.md) is not used as it will always return an empty list of instructions. This is because no instruction can be run after a return statement, and the [next\_instruction()](../instruction/instruction.next\_instruction.md) is intraprocedural.
