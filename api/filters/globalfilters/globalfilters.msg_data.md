# GlobalFilters.MSG\_DATA

The MSG\_DATA property is used to add a filter to include or exclude functions that calls `msg.data`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.MSG_DATA)
    .exec(1)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.39.53 PM.png" alt=""><figcaption></figcaption></figure>
