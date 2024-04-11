# Instructions.library\_calls()

**`library_calls`**`() →` [`Instructions`](./)

Returns a list of all library call instructions.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of library calls instructions instructions
  instructions = Instructions().library_calls().exec(1)

  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "ERC721",
  "sol_function": "function tokenURI(uint256 tokenId) public view virtual override returns (string memory) {
        require(_exists(tokenId),"ERC721Metadata: URI query for nonexistent token");

        string memory baseURI = _baseURI();
        return bytes(baseURI).length > 0 ? string(abi.encodePacked(baseURI,tokenId.toString())) : "";
    }",
  "sol_instruction": "return bytes(baseURI).length > 0 ? string(abi.encodePacked(baseURI,tokenId.toString())) : """
}
```

This outputs the call to the `toString()` library function.
