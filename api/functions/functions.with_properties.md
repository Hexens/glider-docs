---
description: Filter functions satisfying the given expression
---

# Functions.with\_properties()

`with_properties(expr) ->` [`Functions`](../callables/functions/)

E.g: `expr = FunctionFilters.HAS_ARGS & ~FunctionFilters.IS_CONSTRUCTOR` `with_properties(expr)` will return functions that have arguments and are not a constructor.

## Query Example

```python
from glider import *

def query():
    return (
        Functions()
        .with_properties(FunctionFilters.IS_EXTERNAL | FunctionFilters.IS_PUBLIC)
        .exec(10)
    )
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-09 at 12.50.39 PM.png" alt=""><figcaption></figcaption></figure>
