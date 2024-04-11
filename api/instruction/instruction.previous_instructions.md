---
description: >-
  Returns a list of the previous instructions of the current node in the control
  flow graph.
---

# Instruction.previous\_instructions()

Query

```python
from glider import *
def query():
  instructions = Instructions().exec(1,20)
  return instructions[0].previous_instructions()
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "function _setOwner(address newOwner) private {\n        address oldOwner = _owner;\n        _owner = newOwner;\n        emit OwnershipTransferred(oldOwner,newOwner);\n    }",
  "sol_instruction": "{address oldOwner = _owner;\n        _owner = newOwner;\n        emit OwnershipTransferred(oldOwner,newOwner);\n    }"
}
```
