# GlobalFilters.BLOCK\_GAS\_LIMIT

The BLOCK\_GAS\_LIMIT property is used to add a filter to include or exclude functions that calls `block.gaslimit`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.BLOCK_GAS_LIMIT)
    .exec(1, 4)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.18.43 PM.png" alt=""><figcaption></figcaption></figure>
