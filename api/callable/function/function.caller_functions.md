---
description: Returns a Functions object that represents functions that call the function.
---

# Function.caller\_functions()

`caller_functions() →` [`Functions`](../../callables/functions/)

The caller functions are the functions that directly call the specified function.

## Example

```python
from glider import *

def query():
  # Retrieve a function with name _afterTokenTransfer
  functions = Functions().with_name('_afterTokenTransfer').exec(1)

  # Return its caller functions
  return functions[0].caller_functions().exec()
```

## Output

```solidity
"root":{3 items
"contract":string"0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
"contract_name":string"ERC721"
"sol_function":solidity
function _mint(address to, uint256 tokenId) internal virtual {
        require(to != address(0), "ERC721: mint to the zero address");
        require(!_exists(tokenId), "ERC721: token already minted");

        _beforeTokenTransfer(address(0), to, tokenId, 1);

        // Check that tokenId was not minted by `_beforeTokenTransfer` hook
        require(!_exists(tokenId), "ERC721: token already minted");

        unchecked {
            // Will not overflow unless all 2**256 token ids are minted to the same owner.
            // Given that tokens are minted one by one, it is impossible in practice that
            // this ever happens. Might change if we allow batch minting.
            // The ERC fails to describe this case.
            _balances[to] += 1;
        }

        _owners[tokenId] = to;

        emit Transfer(address(0), to, tokenId);

        _afterTokenTransfer(address(0), to, tokenId, 1);
    }
},
"root":{3 items
"contract":string"0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
"contract_name":string"ERC721"
"sol_function":solidity
function _burn(uint256 tokenId) internal virtual {
        address owner = ERC721.ownerOf(tokenId);

        _beforeTokenTransfer(owner, address(0), tokenId, 1);

        // Update ownership in case tokenId was transferred by `_beforeTokenTransfer` hook
        owner = ERC721.ownerOf(tokenId);

        // Clear approvals
        delete _tokenApprovals[tokenId];

        unchecked {
            // Cannot overflow, as that would require more tokens to be burned/transferred
            // out than the owner initially received through minting and transferring in.
            _balances[owner] -= 1;
        }
        delete _owners[tokenId];

        emit Transfer(owner, address(0), tokenId);

        _afterTokenTransfer(owner, address(0), tokenId, 1);
    }
}
```



