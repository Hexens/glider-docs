---
description: >-
  Returns an Instructions object for the assembly instructions of the
  function/modifier.
---

# Callable.asm\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  asm_instructions = []
  for function in functions:
    for instruction in function.asm_instructions().exec():
      # Return the assembly instructions for each function
      asm_instructions.append(instruction)

  return asm_instructions
```

## Example output

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "ERC721",
    // Formatted for the example
    "sol_function": `
    function _checkOnERC721Received(
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
      }
    `,
    // Formatted for the example
    "sol_instruction": `
    assembly {
        revert(add(32,reason),mload(reason))
    }
    `
  },
  ...
]
```
