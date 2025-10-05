# GlobalFilters.BLOCK\_NUMBER

The BLOCK\_NUMBER property is used to add a filter to include or exclude functions that calls `block.number`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.BLOCK_NUMBER)
    .exec(1, 4)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.30.49 PM.png" alt=""><figcaption></figcaption></figure>
