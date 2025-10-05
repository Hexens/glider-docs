# GlobalFilters.BLOCK\_COINBASE

The BLOCK\_COINBASE property is used to add a filter to include or exclude functions that calls `block.coinbase`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.BLOCK_COINBASE)
    .exec(1, 4)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.28.03 PM.png" alt=""><figcaption></figcaption></figure>
