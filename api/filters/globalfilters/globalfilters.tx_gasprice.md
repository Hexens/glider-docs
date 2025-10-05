# GlobalFilters.TX\_GASPRICE

The TX\_GASPRICE property is used to add a filter to include or exclude functions that calls `tx.gasprice`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.TX_GASPRICE)
    .exec(1)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 2.16.40 PM.png" alt=""><figcaption></figcaption></figure>
