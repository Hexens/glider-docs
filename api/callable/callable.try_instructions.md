---
description: Returns try instructions of the function/modifier.
---

# Callable.try\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  try_instructions = []
  for function in functions:
    for instruction in function.try_instructions():
      # Return the try instructions for each function
      try_instructions.append(instruction)

  return try_instructions
```

## Example output

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "ERC721",
    "sol_function": `
    // Formatted for the example
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
    "sol_instruction": `
    // Formatting for the example
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
    `
  },
  ...
]
```
