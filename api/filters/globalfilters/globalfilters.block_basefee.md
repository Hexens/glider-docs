# GlobalFilters.BLOCK\_BASEFEE

The BLOCK\_BASEFEE property is used to add a filter to include or exclude functions that calls `block.basefee`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.BLOCK_BASEFEE)
    .exec(1)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.30.02 PM.png" alt=""><figcaption></figcaption></figure>
