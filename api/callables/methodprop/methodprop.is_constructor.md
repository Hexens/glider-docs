# MethodProp.IS\_CONSTRUCTOR

A constructor function in a smart contract is called when the smart contract is instantiated, and can be used to set initial values of state variables within the contract

An example of a smart contract with a constructor is:

```solidity
contract Example {
    
    constructor(){
    	owner = msg.sender;
    }
    
 }
```

An example of a query which will select constructor functions is:

```python
from glider import *
def query():
  props_included = [MethodProp.IS_CONSTRUCTOR]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
