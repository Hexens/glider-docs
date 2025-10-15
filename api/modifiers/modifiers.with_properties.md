---
description: Filter modifiers satisfying the given expression
---

# Modifiers.with\_properties()

`with_properties(expr) ->`` ``Modifiers`

E.g: `expr = FunctionFilters.HAS_ARGS & ~FunctionFilters.HAS_ERRORS` `with_properties(expr)` will return modifiers that have arguments and don't return errors.

### Query Example

```python
from glider import *

def query():
    return (
        Modifiers()
        .with_properties(FunctionFilters.HAS_GLOBAL_VARIABLES_READ | FunctionFilters.HAS_ERRORS)
        .exec(10)
    )

```

### Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-09 at 12.55.54 PM.png" alt=""><figcaption></figcaption></figure>
