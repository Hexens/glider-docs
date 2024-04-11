# MethodProp.PUBLIC

This property will filter for functions that are exposed in a smart contract and marked with an access level of public. Adding this property filter to the query will add a filter for all functions with this property.

Functions declared with public access are callable from an external third party and from within the smart contract functions.

```solidity
function myFunction(uint256 investAmount) public {}
```

An example of a query that would filter for functions that are marked as public is:

```python
from glider import *
def query():
  props_included = [MethodProp.PUBLIC]
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
function renounceOwnership() public virtual onlyOwner {
        _setOwner(address(0));
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Ownable"
"sol_function":solidity
function transferOwnership(address newOwner) public virtual onlyOwner {
        require(newOwner != address(0),"Ownable: new owner is the zero address");
        _setOwner(newOwner);
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"ERC165"
"sol_function":solidity
function supportsInterface(bytes4 interfaceId) public view virtual override returns (bool) {
        return interfaceId == type(IERC165).interfaceId;
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
```
