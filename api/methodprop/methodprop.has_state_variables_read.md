# MethodProp.HAS\_STATE\_VARIABLES\_READ

If a variable is declared outside of a function within a smart contract it is considered a STATE variable. Such variable's values are stored on the blockchain, for instance account balances and admin addresses.

An example of a query which will select functions that read STATE variables from within the code of the function is:

```python
from glider import *
def query():
  props_included = [MethodProp.HAS_STATE_VARIABLES_READ]
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
function owner() public view virtual returns (address) {
        return _owner;
    }
}
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
function balanceOf(address owner) public view virtual override returns (uint256) {
        require(owner != address(0),"ERC721: balance query for the zero address");
        return _balances[owner];
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"ERC721"
"sol_function":solidity
function ownerOf(uint256 tokenId) public view virtual override returns (address) {
        address owner = _owners[tokenId];
        require(owner != address(0),"ERC721: owner query for nonexistent token");
        return owner;
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"ERC721"
"sol_function":solidity
function name() public view virtual override returns (string memory) {
        return _name;
    }
}
```
