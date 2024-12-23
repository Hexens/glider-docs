# MethodProp.HAS\_STATE\_VARIABLES\_READ

If a variable is declared outside of a function within a smart contract it is considered a STATE variable. Such variable's values are stored on the blockchain, for instance account balances and admin addresses.

An example of a query which will select functions that read STATE variables from within the code of the function is:

```python
from glider import *
def query():
  props_included = [MethodProp.HAS_STATE_VARIABLES_READ]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>
