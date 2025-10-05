---
description: Returns parent function/modifier of the local variable.
---

# LocalVariable.get\_parent()

`get_parent() →` [`Callable`](../../../callable/)

## Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_name("communityMint")
    .exec(1)
  )

  for func in functions:
    local_vars = func.local_variables().list()
    for local_var in local_vars:
      print(local_var.get_parent())

  return functions
```

## Example Output

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-10 at 4.03.52 PM.png" alt=""><figcaption></figcaption></figure>
