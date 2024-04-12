---
description: Returns true if it is an equality check, otherwise returns false.
---

# Condition.is\_eq()

```python
from glider import *

def query():
  functions = Functions().with_name_prefix('checkIf').exec(1,3)
  for func in functions:
    if_instructions = func.if_instructions().exec() # api.instructions.IfInstruction's instance
    if(len(if_instructions) > 0):
      print(if_instructions[0].source_code())
      # This will print True if the comparison operators is equal ("==")
      print(if_instructions[0].get_condition().is_eq())
  return functions
```

Outputs:

```solidity
"root":{3 items
"contract":string"0xf2854d84d9dd27eccd6ab20b3f66111a51bb56d2"
"contract_name":string"UniswapV3PositionTracker"
"sol_function":solidity
function checkIfPositionIsInTracker(
        address caller,
        uint256 tokenId,
        ERC20 token0,
        ERC20 token1
    ) public view returns (bool tokenFound) {
        // Search through caller's holdings and return true if the token id was found.
        uint256[] storage holdings = callerToToken0ToToken1ToHoldings[caller][token0][token1];
        uint256 holdingLength = holdings.length;
 
        for (uint256 i; i < holdingLength; ++i) {
            uint256 currentTokenId = holdings[i];
            if (currentTokenId == tokenId) {
                return true;
            }
        }
 
        // If we made it this far the LP token was not found.
        return false;
    }
},
"root":{1 item
    "print_output":[2 items
    0:string"currentTokenId == tokenId"
    1:string"True"
    ]
}
```
