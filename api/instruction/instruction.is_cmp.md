---
description: >-
  Returns True if the instruction is a comparison instruction i.e performing
  comparison operation/s using operators like >, <, == etc.., otherwise returns
  False.
---

# Instruction.is\_cmp()

Query

```python
from glider import *
def query():
  comparisons = []
  #fetch a list of instructions
  instructions = Instructions().exec(30)
  for instruction in instructions:
    #check if instruction is a comparison instruction
    if(instruction.is_cmp()):
      comparisons.append(instruction)  
  return comparisons
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "ERC165",
  "sol_function": "function supportsInterface(bytes4 interfaceId) public view virtual override returns (bool) {\n        return interfaceId == type(IERC165).interfaceId;\n    }",
  "sol_instruction": "return interfaceId == type(IERC165).interfaceId"
}
```
