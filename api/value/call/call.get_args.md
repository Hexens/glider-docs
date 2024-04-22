---
description: >-
  Returns the arguments of the call, or empty array if the call has no
  arguments.
---

# Call.get\_args()

`get_args() → List[`[`Value`](../)`]`



## Query Example

```python
from glider import *

def query():
  instructions = (
    Contracts().
    non_interface_contracts().
    functions().
    instructions().
    exec(1,2)
  )

  output = []

  for entry_ins in instructions:
    for next_ins in entry_ins.next_instructions():
      for call in next_ins.get_callee_values():
          output.append(next_ins)
          for arg in call.get_args():
            print(arg, arg.expression)

  return output
```

## Output&#x20;

```solidity
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function add(uint256 a, uint256 b) internal pure returns (uint256) {
        uint256 c = a + b;
        require(c >= a, "SafeMath: addition overflow");
        return c;
    }
"sol_instruction":solidity
require(c >= a, "SafeMath: addition overflow")
}
"root":{1 item
"print_output":[4 items
0:string"<api.value.ConditionalExpression object at 0x7ff192f4d150>"
1:string"c >= a"
2:string"<api.value.Literal object at 0x7ff192f4e350>"
3:string""SafeMath: addition overflow""
]
}
```
