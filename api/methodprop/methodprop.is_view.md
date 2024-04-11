# MethodProp.IS\_VIEW

In a smart contract a function can be declared that will not modify any state variable values. These functions are marked as VIEW functions

An example of a view function is:

```solidity
function getOwner() external view returns address {
	return owner;
}
```

An example of a query that would select only VIEW functions is:

```python
from glider import *
def query():
  props_included = [MethodProp.IS_VIEW]
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
function owner() public view virtual returns (address) {
        return _owner;
    }
}
```
