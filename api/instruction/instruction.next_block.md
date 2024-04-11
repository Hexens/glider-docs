---
description: >-
  Returns the list of instructions following the current instruction till the
  branching point.
---

# Instruction.next\_block()

Query

```python
from glider import *
def query():
  instructions = Instructions().exec(1,19)
  return instructions[0].next_block()
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "function _setOwner(address newOwner) private {\n        address oldOwner = _owner;\n        _owner = newOwner;\n        emit OwnershipTransferred(oldOwner,newOwner);\n    }",
  "sol_instruction": "address oldOwner = _owner"
}

{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "function _setOwner(address newOwner) private {\n        address oldOwner = _owner;\n        _owner = newOwner;\n        emit OwnershipTransferred(oldOwner,newOwner);\n    }",
  "sol_instruction": "_owner = newOwner"
}

{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "function _setOwner(address newOwner) private {\n        address oldOwner = _owner;\n        _owner = newOwner;\n        emit OwnershipTransferred(oldOwner,newOwner);\n    }",
  "sol_instruction": "emit OwnershipTransferred(oldOwner,newOwner)"
}
```

The output shows that the query returns all the instructions in the \_setOwner() function
