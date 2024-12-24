# MethodProp.HAS\_STATE\_VARIABLES\_WRITTEN

If a variable is declared outside of a function within a smart contract it is considered a STATE variable. Such variable's value are stored permanently on the blockchain, for instance account balances and admin addresses.

An example of a query which will select functions that modify STATE variables from within the code of the function is:

```python
from glider import *
def query():
  props_included = [MethodProp.HAS_STATE_VARIABLES_WRITTEN]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>
