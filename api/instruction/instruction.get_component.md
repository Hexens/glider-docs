---
description: Returns the instruction's i-th component.
---

# Instruction.get\_component()

`get_component(`_`i : int`_`) →` [`Value`](../value/) `|` [`NoneObject`](../internal/noneobject/)

## Query Example

```python
from glider import *

def query():
    instructions = Instructions().exec(1,1)
  
    print(instructions[0].get_component(0).expression)
    return instructions
```

## Output Example

```solidity
[
  {
    "contract": "0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb",
    "contract_name": "Context",
    "contract_link": "",
    "uuid": "7cb07206-158e-4511-bb3b-f42d01a53bcf",
    "severity": "",
    "sol_function": 
      function _msgSender() internal view virtual returns (address payable) {
          return msg.sender;
      }
    "sol_instruction": 
      return msg.sender
  },
  {
    "print_output": [
      "msg.sender"
    ]
  }
]
```
