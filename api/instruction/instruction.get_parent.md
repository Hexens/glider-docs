---
description: Returns parent function/modifier of the instruction.
---

# Instruction.get\_parent()

```python
from glider import *
def query():
  #return the parent function/modifier of an instruction
  return [Instructions().exec(1)[0].get_parent()]
```

Output

```json
{
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD", 
    "contract_name": "Context", 
    "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }"
}
```
