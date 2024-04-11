# MethodProp.IS\_CONSTRUCTOR

A constructor function in a smart contract is called when the smart contract is instantiated, and can be used to set initial values of state variables within the contract

An example of a smart contract with a constructor is:

```solidity
contract Example {
    
    constructor(){
    	owner = msg.sender;
    }
    
 }
```

An example of a query which will select constructor functions is:

```python
from glider import *
def query():
  props_included = [MethodProp.IS_CONSTRUCTOR]
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
constructor() {
        _setOwner(_msgSender());
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
"contract_name":string"ERC721URIStorage"
"sol_function":solidity
constructor(string memory name_,string memory symbol_) {
        _name = name_;
        _symbol = symbol_;
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"LTP"
"sol_function":solidity
constructor(string memory name_,string memory symbol_) {
        _name = name_;
        _symbol = symbol_;
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"LTP"
"sol_function":solidity
constructor() {
        _setOwner(_msgSender());
    }
}
```
