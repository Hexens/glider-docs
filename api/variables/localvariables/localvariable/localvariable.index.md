---
description: Returns the index of the local variable in relation to the function scope.
---

# LocalVariable.index

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
      print(local_var.source_code())
      print(local_var.index)

  return functions
```

## Example Output

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-10 at 4.50.47 PM.png" alt=""><figcaption></figcaption></figure>
