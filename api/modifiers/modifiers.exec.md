# Modifiers.exec()

Executes the formed query and returns a list of the [Modifier](../modifier/) objects.

## Return type

→ List\[[Modifier](../modifier/)]

It accepts two integer parameters the first one is `limit_count` which limits the count of the returned results and the second is `offset_count` which sets the offset from which the result set must be returned.

&#x20;In specific in the Modifiers scenario it will action a query to search for modifiers.

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

An example of a query which adds a filter to select functions which have modifiers with the name "onlyOwner" is:

```python
from glider import *
def query():
  modifierlist = Modifiers()\
      .with_name("onlyOwner")\
      .exec(5)
  return modifierlist
```

## Output

```json
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Ownable"
"sol_modifier":solidity
modifier onlyOwner() {
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"LTP"
"sol_modifier":solidity
modifier onlyOwner() {
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
}
"root":{3 items
"contract":string"0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2"
"contract_name":string"Owned"
"sol_modifier":solidity
modifier onlyOwner {
        _onlyOwner();
        _;
    }
}
"root":{3 items
"contract":string"0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2"
"contract_name":string"RewardsDistributionRecipient"
"sol_modifier":solidity
modifier onlyOwner {
        _onlyOwner();
        _;
    }
}
"root":{3 items
"contract":string"0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2"
"contract_name":string"Pausable"
"sol_modifier":solidity
modifier onlyOwner {
        _onlyOwner();
        _;
    }
}
```
