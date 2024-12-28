# MethodProp.IS\_PAYABLE

In a smart contract a function can be marked as payable. This means that the function can accept the native token of the chain as a payment value.

An example  of a payable function is

```solidity
function depositETH() external payable {
	depositor[msg.sender].balance = msg.value;
}
```

An example of a query which would select all payable functions is:

```python
from glider import *
def query():
  props_included = [MethodProp.IS_PAYABLE]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
