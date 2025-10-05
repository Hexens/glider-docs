# GlobalFilters.BLOCK\_PREVRANDAO

The BLOCK\_PREVRANDAO property is used to add a filter to include or exclude functions that calls `block.prevrandao`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.BLOCK_PREVRANDAO)
    .exec(1, 4)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.36.04 PM.png" alt=""><figcaption></figcaption></figure>
