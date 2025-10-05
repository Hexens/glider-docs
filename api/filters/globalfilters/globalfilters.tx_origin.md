# GlobalFilters.TX\_ORIGIN

The TX\_ORIGIN property is used to add a filter to include or exclude functions that calls `tx.origin`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.TX_ORIGIN)
    .exec(1, 2)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 2.20.14 PM.png" alt=""><figcaption></figcaption></figure>
