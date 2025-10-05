# GlobalFilters.MSG\_SIG

The MSG\_SIG property is used to add a filter to include or exclude functions that calls `msg.sig`.&#x20;

### Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_globals(GlobalFilters.MSG_SIG)
    .exec(1)
  )
  
  return functions
```

### Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-08-28 at 12.46.37 PM.png" alt=""><figcaption></figcaption></figure>
