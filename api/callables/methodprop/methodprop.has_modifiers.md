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

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
