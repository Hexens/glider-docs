---
description: Returns an Instructions object for the 'assembly' instructions
---

# Instructions.asm\_instructions()

## Function Signature

**`asm_instructions`**`() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  # Fetch a list of assembly instructions
  instructions = Instructions().asm_instructions().exec(1)
  
  return instructions
```

## Output Example

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "ERC721",
  "sol_function": "function _checkOnERC721Received(
        address from,address to,uint256 tokenId,bytes memory _data
    ) private returns (bool) {
        if (to.isContract()) {
            try IERC721Receiver(to).onERC721Received(_msgSender(),from,tokenId,_data) returns (bytes4 retval) {
                return retval == IERC721Receiver.onERC721Received.selector;
            } catch (bytes memory reason) {
                if (reason.length == 0) {
                    revert("ERC721: transfer to non ERC721Receiver implementer");
                } else {
                    assembly {
                        revert(add(32,reason),mload(reason))
                    }
                }
            }
        } else {
            return true;
        }
    }",
  "sol_instruction": "assembly {
                        revert(add(32,reason),mload(reason))
                    }"
}
```
