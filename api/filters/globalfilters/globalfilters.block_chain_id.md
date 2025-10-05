# GlobalFilters.BLOCK\_CHAIN\_ID

The BLOCK\_CHAIN\_ID property is used to add a filter to include or exclude functions that calls `block.chainid`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.BLOCK_CHAIN_ID)
    .exec(1)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.29.01 PM.png" alt=""><figcaption></figcaption></figure>
