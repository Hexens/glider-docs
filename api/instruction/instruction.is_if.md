---
description: Returns true if the instruction is an if instruction, otherwise returns false.
---

# Instruction.is\_if()

Query

```python
from glider import *
def query():
  ifs = []
  #fetch a list of instructions
  instructions = Instructions().exec(100)
  for instruction in instructions:
    #check if instruction is an if instruction
    if(instruction.is_if()):
      ifs.append(instruction)  
  return ifs
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "ERC721",
  "sol_function": "function tokenURI(uint256 tokenId) public view virtual override returns (string memory) {\n        require(_exists(tokenId),\"ERC721Metadata: URI query for nonexistent token\");\n\n        string memory baseURI = _baseURI();\n        return bytes(baseURI).length > 0 ? string(abi.encodePacked(baseURI,tokenId.toString())) : \"\";\n    }",
  "sol_instruction": "return bytes(baseURI).length > 0 ? string(abi.encodePacked(baseURI,tokenId.toString())) : \"\""
}
```
