# MethodProp.PRIVATE

This property will filter for functions that are exposed in a smart contract and marked with an access level of private

Functions declared with private access are callable only from functions inside of the smart contract and not by any child contracts. In solidity a function that has access set as private will have a similar signature to this one:

```solidity
function myFunction(uint256 investAmount) private {}
```

An example of a query that would filter for functions that are marked as internal is:

```python
from glider import *
def query():
  props_included = [MethodProp.PRIVATE]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption></figcaption></figure>
