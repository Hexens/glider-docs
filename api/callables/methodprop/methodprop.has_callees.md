# MethodProp.HAS\_CALLEES

The property HAS\_CALLEES is used to add a filter to include or exclude functions that have functions that call them from within the same contract.

An example of a query which will filter for functions that have callees is:

```python
from glider import *
def query():
  props_included = [MethodProp.HAS_CALLEES]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>
