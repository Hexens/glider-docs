# GlobalFilters.BLOCK\_DIFFICULTY

The BLOCK\_DIFFICULTY property is used to add a filter to include or exclude functions that calls `block.difficulty`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.BLOCK_DIFFICULTY)
    .exec(1, 4)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.25.23 PM.png" alt=""><figcaption></figcaption></figure>
