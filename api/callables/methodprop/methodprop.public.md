# MethodProp.PUBLIC

This property will filter for functions that are exposed in a smart contract and marked with an access level of public. Adding this property filter to the query will add a filter for all functions with this property.

Functions declared with public access are callable from an external third party and from within the smart contract functions.

```solidity
function myFunction(uint256 investAmount) public {}
```

An example of a query that would filter for functions that are marked as public is:

```python
from glider import *
def query():
  props_included = [MethodProp.PUBLIC]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (179).png" alt=""><figcaption></figcaption></figure>
