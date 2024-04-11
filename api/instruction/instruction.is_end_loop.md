---
description: >-
  Returns true if the instruction is end_loop instruction, otherwise returns
  false.
---

# Instruction.is\_end\_loop()

Query

```python
from glider import *
def query():
  end_loops = []
  #fetch a list of instructions
  instructions = Instructions().exec(525)
  for instruction in instructions:
    #check if instruction is an end_loop instruction
    if(instruction.is_end_loop()):
      end_loops.append(instruction)  
  return end_loops
```

Output

```
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Strings",
  "sol_function": "function toString(uint256 value) internal pure returns (string memory) {\n        \n        \n\n        if (value == 0) {\n            return \"0\";\n        }\n        uint256 temp = value;\n        uint256 digits;\n        while (temp != 0) {\n            digits++;\n            temp /= 10;\n        }\n        bytes memory buffer = new bytes(digits);\n        while (value != 0) {\n            digits -= 1;\n            buffer[digits] = bytes1(uint8(48 + uint256(value % 10)));\n            value /= 10;\n        }\n        return string(buffer);\n    }",
  "sol_instruction": "while (temp != 0) {\n            digits++;\n            temp /= 10;\n        }"
}
```
