---
description: Returns the instruction's components.
---

# Instruction.get\_components()

`get_components() →` [`APIList`](../iterables/apilist.md)`[`[`Value`](../value/) `|` [`NoneObject`](../internal/noneobject/)`]`

## Query Example

```python
from glider import *

def query():
    instructions = Instructions().exec(1,10)
    for inst in instructions:
        for component in inst.get_components():
            print(component.expression)

    return instructions
```

## Output Example

```solidity
[
  {
    "contract": "0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "contract_name": "REBITCOIN",
    "contract_link": "https://etherscan.io/address/0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "uuid": "45eaade2-f058-46e0-84a3-12393287f88e",
    "severity": "",
    "sol_function": 
      function balanceOf(address _owner) constant returns (uint256 balance) 
       {
          return balances[_owner];
       }
    "sol_instruction": 
      return balances[_owner]
  },
  {
    "print_output": [
      "balances",
      "[]",
      "_owner"
    ]
  }
]
```
