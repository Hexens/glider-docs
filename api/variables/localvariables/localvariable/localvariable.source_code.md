---
description: Returns the source code of the local variable.
---

# LocalVariable.source\_code()

`source_code() → str`

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

  return functions
```

## Example Output

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-10 at 4.52.00 PM.png" alt=""><figcaption></figcaption></figure>
