# MethodProp.EXTERNAL

This property will filter for functions that are exposed in a smart contract and marked with an access level of external. Adding this property filter to the query will add a filter for all functions with this property.&#x20;

Functions declared with external access are callable from an external third party.

In solidity a function that has access set as external will have a similar signature to this one:

```solidity
function myFunction(uint256 investAmount) external {}
```

An example of such a query would be:

```python
from glider import *
def query():
  props_any = [MethodProp.EXTERNAL]
  functions = Functions()\
      .with_one_property(props_any)\
      .exec(5)

  return functions
```

## Output

```json
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"IERC165"
"sol_function":solidity
function supportsInterface(bytes4 interfaceId) external view returns (bool);
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"IERC721"
"sol_function":solidity
function supportsInterface(bytes4 interfaceId) external view returns (bool);
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"IERC721"
"sol_function":solidity
function balanceOf(address owner) external view returns (uint256 balance);
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"IERC721"
"sol_function":solidity
function ownerOf(uint256 tokenId) external view returns (address owner);
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"IERC721"
"sol_function":solidity
function safeTransferFrom(
        address from,address to,uint256 tokenId
    ) external;
}
```
