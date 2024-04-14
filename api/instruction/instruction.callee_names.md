---
description: >-
  Returns the list of function names that are called from the instruction. It
  returns an empty list for an instruction that does not call any functions
---

# Instruction.callee\_names()

`callee_names() → List[str]`

For example, for the instruction:

```solidity
require(!_exists(tokenId), "ERC721: token already minted");
```

The functions will return `['_exists', 'require']`

## Query Example

```python
from glider import *
def query():
  #fetch an instruction
  instruction = Instructions().with_callee_function_name('require').exec(1,30)
  #print the list of function names called from the instruction
  print(instruction[0].callee_names()) 
  return instruction
```

## Output

```solidity
"root":{4 items
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
"sol_instruction":solidity
require(!_exists(tokenId), "ERC721: token already minted")
}
"root":{1 item
"print_output":[1 item
0:string"['_exists', 'require']"
]
}
```
