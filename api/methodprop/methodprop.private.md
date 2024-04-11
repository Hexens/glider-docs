# MethodProp.PRIVATE

This property will filter for functions that are exposed in a smart contract and marked with an access level of private

Functions declared with private access are callable only from functions inside of the smart contract and not by any child contracts. In solidity a function that has access set as private will have a similar signature to this one:

```solidity
function myFunction(uint256 investAmount) private {}
```

An example of a query that would filter for functions that are marked as internal is:

```python
from glider import *
def query():
  props_included = [MethodProp.PRIVATE]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

```json
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Context"
"sol_function":solidity
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Context"
"sol_function":solidity
function _msgData() internal view virtual returns (bytes calldata) {
        return msg.data;
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Ownable"
"sol_function":solidity
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Ownable"
"sol_function":solidity
function _msgData() internal view virtual returns (bytes calldata) {
        return msg.data;
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Ownable"
"sol_function":solidity
constructor() {
        _setOwner(_msgSender());
    }
}
```
