---
description: Executes the formed query and returns the list of Instruction objects
---

# Instructions.exec()

`exec(limit_count: int = 0, offset_count: int = 0) →` [`APIList`](../iterables/apilist.md)`[`[`Instruction`](../instruction/)`]`

`limit_count` is the number of instructions to query, while `offset_count` is the offset applied to the results returned. For example with `offset_count` = 2, will return `limit_count` instructions starting from the 3rd instructions.

## Return type

`→` [`APIList`](../iterables/apilist.md)`[`[`Instruction`](../instruction/)`]`

## Query Example

```python
from glider import *

def query():
  # Fetch a list of instructions
  instructions = Instructions().exec(2)
  
  return instructions
```

## Output Example

```solidity
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": 
        function _msgSender() internal view virtual returns (address) {
            return msg.sender;
        },
    "sol_instruction": 
        {
            return msg.sender;
        }
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": 
        function _msgSender() internal view virtual returns (address) {
            return msg.sender;
        },
    "sol_instruction": 
        {
            return msg.sender"
        }
  }
]
```
