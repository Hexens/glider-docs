---
description: Returns True if the instruction is break instruction, otherwise returns False.
---

# Instruction.is\_break()

Query

```python
from glider import *
def query():
  breaks = []
  #fetch a list of instructions
  instructions = Instructions().exec(1350) 
  for instruction in instructions:
    #check if an instruction is a break instruction
    if(instruction.is_break()):
      breaks.append(instruction) 
  return breaks
```

Output

```json
{
  "contract": "0x561ae3768ee95987b355c287f985f2838f01e632",
  "contract_name": "PBX",
  "sol_function": "function includeInReward(address account) external onlyOwner() {\n        require(_isExcluded[account],\"Account is already included\");\n        require(account != address(0),\"Address is not valid\");\n        for (uint256 i = 0; i < _excluded.length; i++) {\n            if (_excluded[i] == account) {\n                _excluded[i] = _excluded[_excluded.length - 1];\n                _tOwned[account] = 0;\n                _isExcluded[account] = false;\n                _excluded.pop();\n                break;\n            }\n        }\n    }",
  "sol_instruction": "break"
}
```
