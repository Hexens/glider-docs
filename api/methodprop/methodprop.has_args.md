# MethodProp.HAS\_ARGS

The HAS\_ARGS property adds a filter to either include or exclude functions that have arguments in their signature.

An example of a function with a signature would be&#x20;

```solidity
function myFunction(uint256 investAmount){}
```

In the example below the query will filter out all functions that have arguments and only return those functions with no arguments in their signature

```python
from glider import *

def query():
  props_excluded = [MethodProp.HAS_ARGS]

  functions = Functions()\
      .without_properties(props_excluded)\
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
