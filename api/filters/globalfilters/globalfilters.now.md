# GlobalFilters.NOW

The NOW property is used to add a filter to include or exclude functions that calls `now`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.NOW)
    .exec(1)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.49.11 PM.png" alt=""><figcaption></figcaption></figure>
