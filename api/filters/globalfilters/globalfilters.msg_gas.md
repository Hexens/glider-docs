# GlobalFilters.MSG\_GAS

The MSG\_GAS property is used to add a filter to include or exclude functions that calls `msg.gas`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.MSG_GAS)
    .exec(1)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.42.10 PM.png" alt=""><figcaption></figcaption></figure>
