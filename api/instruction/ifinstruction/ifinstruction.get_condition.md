# IfInstruction.get\_condition()

`get_condition() →` [`Condition`](../../condition/)

Returns condition of the if-statement.

## Example

```python
from glider import *

def query():
  instructionlist = Instructions().if_instructions().exec(1)
  
  condition = instructionlist[0].get_condition()
  print(condition.is_eq())
  return instructionlist
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
a == 0
},
"root":{1 item
"print_output":[1 item
0:string"True"
]
}
```

