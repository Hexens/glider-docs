# Instructions.if\_statements()

**`if_statements`**`() →` [`Instructions`](./)

Returns an [Instructions](./) object for the if instructions.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of if statement instructions
  instructions = Instructions().if_statements().exec(2)

  return instructions
```

Output:

```json
[
    {
      "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
      "contract_name": "ERC721",
      "sol_function": "function tokenURI(uint256 tokenId) public view virtual override returns (string memory) {
            require(_exists(tokenId),"ERC721Metadata: URI query for nonexistent token");
    
            string memory baseURI = _baseURI();
            return bytes(baseURI).length > 0 ? string(abi.encodePacked(baseURI,tokenId.toString())) : "";
        }",
      "sol_instruction": "return bytes(baseURI).length > 0 ? string(abi.encodePacked(baseURI,tokenId.toString())) : """
    },
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
      "sol_instruction": "to.isContract()"
    }
]
```

Note that the ternary operator is included as well.
