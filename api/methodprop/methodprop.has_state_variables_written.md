# MethodProp.HAS\_STATE\_VARIABLES\_WRITTEN

If a variable is declared outside of a function within a smart contract it is considered a STATE variable. Such variable's value are stored permanently on the blockchain, for instance account balances and admin addresses.

An example of a query which will select functions that modify STATE variables from within the code of the function is:

```python
from glider import *
def query():
  props_included = [MethodProp.HAS_STATE_VARIABLES_WRITTEN]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

```json
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Ownable"
"sol_function":solidity
function _setOwner(address newOwner) private {
        address oldOwner = _owner;
        _owner = newOwner;
        emit OwnershipTransferred(oldOwner,newOwner);
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"ERC721"
"sol_function":solidity
constructor(string memory name_,string memory symbol_) {
        _name = name_;
        _symbol = symbol_;
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"ERC721"
"sol_function":solidity
function setApprovalForAll(address operator,bool approved) public virtual override {
        require(operator != _msgSender(),"ERC721: approve to caller");
 
        _operatorApprovals[_msgSender()][operator] = approved;
        emit ApprovalForAll(_msgSender(),operator,approved);
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"ERC721"
"sol_function":solidity
function _mint(address to,uint256 tokenId) internal virtual {
        require(to != address(0),"ERC721: mint to the zero address");
        require(!_exists(tokenId),"ERC721: token already minted");
 
        _beforeTokenTransfer(address(0),to,tokenId);
 
        _balances[to] += 1;
        _owners[tokenId] = to;
 
        emit Transfer(address(0),to,tokenId);
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"ERC721"
"sol_function":solidity
function _burn(uint256 tokenId) internal virtual {
        address owner = ERC721.ownerOf(tokenId);
 
        _beforeTokenTransfer(owner,address(0),tokenId);
 
        
        _approve(address(0),tokenId);
 
        _balances[owner] -= 1;
        delete _owners[tokenId];
 
        emit Transfer(owner,address(0),tokenId);
    }
}
```
