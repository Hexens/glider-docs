---
description: Executes the formed query and returns an APIList of the Modifier objects.
---

# Modifiers.exec()

`exec(`_`limit_count: int = 0`_`,`` `_`offset_count: int = 0`_`) →` [`APIList`](../../iterables/apilist.md)`[`[`Modifier`](../../callable/modifier/)`]`

It accepts two integer parameters: the first one is `limit_count` which limits the count of the returned results, and the second is `offset_count` which sets the offset from which the result set must be returned.

In specific, in the Modifiers scenario, it will action a query to search for modifiers.

In solidity, a smart contract can define modifiers which can be called before the code of the function is run.

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
  modifiers = (
    Modifiers()
      .with_name("onlyOwner")
      .exec(5)
  )

  return modifiers
```

## Output

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
