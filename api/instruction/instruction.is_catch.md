---
description: >-
  Returns True if the instruction is catch instruction in a try-catch block,
  otherwise returns False.
---

# Instruction.is\_catch()

Query

```python
from glider import *
def query():
  catch = []
  #fetch a list of instructions
  instructions = Instructions().exec(1,120)
  for instruction in instructions:
    #check if instruction is a catch instruction
    if(instruction.is_catch()):
      catch.append(instruction)  
  return catch
```

Output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "ERC721",
  "sol_function": "function _checkOnERC721Received(\n        address from,address to,uint256 tokenId,bytes memory _data\n    ) private returns (bool) {\n        if (to.isContract()) {\n            try IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,_data) returns (bytes4 retval) {\n                return retval == IERC721Receiver.onERC721Received.selector;\n            } catch (bytes memory reason) {\n                if (reason.length == 0) {\n                    revert(\"ERC721: transfer to non ERC721Receiver implementer\");\n                } else {\n                    assembly {\n                        revert(add(32,reason),mload(reason))\n                    }\n                }\n            }\n        } else {\n            return true;\n        }\n    }",
  "sol_instruction": "catch (bytes memory reason) {\n                if (reason.length == 0) {\n                    revert(\"ERC721: transfer to non ERC721Receiver implementer\");\n                } else {\n                    assembly {\n                        revert(add(32,reason),mload(reason))\n                    }\n                }\n            }"
}
```
