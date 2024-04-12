---
description: Returns if instructions of the function/modifier.
---

# Callable.if\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  if_instructions = []
  for function in functions:
    for instruction in function.if_instructions().exec():
      if_instructions.append(instruction)

  return if_instructions
```

## Example output

```solidity
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "ERC721URIStorage",
    "sol_function": `
    // Formatted for the example
    function tokenURI(uint256 tokenId) public view virtual override returns (string memory) {
        require(_exists(tokenId),"ERC721URIStorage: URI query for nonexistent token");
        string memory _tokenURI = _tokenURIs[tokenId];
        string memory base = _baseURI();

        if (bytes(base).length == 0) {
            return _tokenURI;
        }

        if (bytes(_tokenURI).length > 0) {
            return string(abi.encodePacked(base,_tokenURI));
        }

        return super.tokenURI(tokenId);
    }
    `,
    "sol_instruction": "bytes(base).length == 0"
  },
  {
    ...
    "sol_instruction": "bytes(_tokenURI).length > 0"
  },
  ...
]
```
