# MethodProp.HAS\_ERRORS

The HAS\_ERRORS property is used to add a filter to include or exclude functions that revert with an error.

In solidity a smart contract a developer can define custom errors which are then called when an error is raised.

An example of such a contract would be as below:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Example {
    error myCustomError(uint256 requestedAmount,address caller);

    function collectAllowance(address caller,uint256 requestedAmount) public returns (bool success){
            //just revert to show how errors work
            revert myCustomError(requestedAmount,caller);
    }

}
```

An example of a query which would filter to include functions that use errors is&#x20;

```python
from glider import *
def query():
  props_included = [MethodProp.HAS_ERRORS]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
