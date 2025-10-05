# GlobalFilters.BLOCK\_TIME\_STAMP

The BLOCK\_TIME\_STAMP property is used to add a filter to include or exclude functions that calls `block.timestamp`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.BLOCK_TIME_STAMP)
    .exec(1)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.38.01 PM.png" alt=""><figcaption></figcaption></figure>
