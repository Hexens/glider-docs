# MethodProp.EXTERNAL

This property will filter for functions that are exposed in a smart contract and marked with an access level of external. Adding this property filter to the query will add a filter for all functions with this property.&#x20;

Functions declared with external access are callable from an external third party.

In solidity a function that has access set as external will have a similar signature to this one:

```solidity
function myFunction(uint256 investAmount) external {}
```

An example of such a query would be:

```python
from glider import *
def query():
  props_any = [MethodProp.EXTERNAL]
  functions = Functions()\
      .with_one_property(props_any)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
