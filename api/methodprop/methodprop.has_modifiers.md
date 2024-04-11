# MethodProp.HAS\_MODIFIERS

In solidity a smart contract can define modifiers which can be called before the code of the function is run.

An example of such a contract would be as below:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Example {
    modifier onlyOwner {
    	require(msg.sender == owner);
    	_;
   	}
   	
   	//This function has the onlyOwner modifier
   	function setNewOwner(address newOwner) public onlyOwner {
   		owner = newOwner;
   	}

}
```



An example of a query which adds a filter to select functions which have modifiers is:

```python
from glider import *
def query():
  props_included = [MethodProp.HAS_MODIFIERS]
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
"contract_name":string"LTP"
"sol_function":solidity
function renounceOwnership() public virtual onlyOwner {
        _setOwner(address(0));
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"LTP"
"sol_function":solidity
function transferOwnership(address newOwner) public virtual onlyOwner {
        require(newOwner != address(0),"Ownable: new owner is the zero address");
        _setOwner(newOwner);
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"LTP"
"sol_function":solidity
function mint() external onlyMinterOrOwner returns (uint256) {
        _mint(address(this),nextId);
        flowRates[nextId] = _testFlowRate;
 
        uint256 ltpId = nextId;
        nextId += 1;
        return ltpId;
    }
}
```
