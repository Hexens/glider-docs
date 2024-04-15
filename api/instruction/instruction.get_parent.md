---
description: Returns parent function/modifier of the instruction.
---

# Instruction.get\_parent()

`get_parent() → Callable | NoneObject`

The function returns a [Callable](../callable/) object, specifically either a [Function](../function/) or [Modifier](../modifier/) object, where the current instruction is placed.

## Query Example

```python
from glider import *
def query():
  #return the parent function/modifier of an instruction
  return [Instructions().exec(1)[0].get_parent()]
```

## Output

```solidity
{
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD", 
    "contract_name": "Context", 
    "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }"
}
```
