---
description: Returns true if it is ">" check, otherwise returns false.
---

# Condition.is\_gr()

```python
from glider import *

def query():
  functions = Functions().with_name_prefix('checkIf').exec(200,200)

  for func in functions:
    if_instructions = func.if_instructions().exec() # api.instructions.IfInstruction's instance
    if len(if_instructions) > 0 and if_instructions[0].get_condition().is_gr():
      print(if_instructions[0].source_code())
      return [func]
  return []
```



Output:

```solidity
"root":{3 items
"contract":string"0x3036193618c41b61adc5cac31e38bfed1e7fcad0"
"contract_name":string"Mjollnir"
"sol_function":solidity
function checkIfBot(address sender, address recipient) private {
        if ((block.number - launchBlock) > snipeBlockAmount) {
            snipeBlockExpired = true;
        } else if (sender != owner() && recipient != owner()) {
            if (!isMarketPair[sender] && sender != address(this)) {
                isEarlyBuyer[sender] = true;
            }
            if (!isMarketPair[recipient] && recipient != address(this)) {
                isEarlyBuyer[recipient] = true;
            }
        }
    }
},
"root":{1 item
"print_output":[1 item
0:string"(block.number - launchBlock) > snipeBlockAmount"
]
}
```
