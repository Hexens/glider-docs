---
description: >-
  Returns true if the instruction has an external dependency on external
  variables, false otherwise.
---

# Instruction.has\_global\_df()

Query

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().exec(5)
  results = []
  #check if the instruction has dependency on a global variable
  for instruction in instructions:
    if instruction.has_global_df():
      res.append(instruction)
  return results
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context",
  "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }",
  "sol_instruction": "return msg.sender"
}
```

