# MethodProp.IS\_PURE

In a smart contract a function can be declared that neither reads nor modifies any state variables. These functions can be marked as PURE functions

An example of such a function is:

```solidity
function add(uint256 a,uint256 b) external pure returns uint256 {
	return a + b;
}
```

An example of a query that would select functions marked as pure functions is:

```python
from glider import *
def query():
  props_included = [MethodProp.IS_PURE]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (8) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
