---
description: Returns a list of immediate previous instructions in the control flow graph.
---

# Instruction.previous\_instruction()

Query

```python
from glider import *
def query():
  instructions = Instructions().exec(1,3)
  return instructions[0].previous_instruction()
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context",
  "sol_function": "function _msgData() internal view virtual returns (bytes calldata) {\n        return msg.data;\n    }",
  "sol_instruction": "{\n        return msg.data;\n    }"
}
```
