---
description: >-
  Returns True if the instruction is an assembly instruction, otherwise returns
  False. Assembly instructions are written in Yul in an assembly block in a
  solidity contract
---

# Instruction.is\_assembly()

Query

```python
from glider import *
def query():
  assembly = []
  #fetch a list of instructions
  instructions = Instructions().exec(150) 
  for instruction in instructions:
    #check if an instruction is an assembly instruction
    if(instruction.is_assembly()):
      assembly.append(instruction) 
  return assembly
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "ERC721",
  "sol_function": "function _checkOnERC721Received(\n        address from,address to,uint256 tokenId,bytes memory _data\n    ) private returns (bool) {\n        if (to.isContract()) {\n            try IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,_data) returns (bytes4 retval) {\n                return retval == IERC721Receiver.onERC721Received.selector;\n            } catch (bytes memory reason) {\n                if (reason.length == 0) {\n                    revert(\"ERC721: transfer to non ERC721Receiver implementer\");\n                } else {\n                    assembly {\n                        revert(add(32,reason),mload(reason))\n                    }\n                }\n            }\n        } else {\n            return true;\n        }\n    }",
  "sol_instruction": "assembly {\n                        revert(add(32,reason),mload(reason))\n                    }"
}
```
