# MethodProp.IS\_VIEW

In a smart contract a function can be declared that will not modify any state variable values. These functions are marked as VIEW functions

An example of a view function is:

```solidity
function getOwner() external view returns address {
	return owner;
}
```

An example of a query that would select only VIEW functions is:

```python
from glider import *
def query():
  props_included = [MethodProp.IS_VIEW]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
