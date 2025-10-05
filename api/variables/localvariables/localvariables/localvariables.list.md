---
description: Returns the list of all local variables.
---

# LocalVariables.list()

`list() →` [`APIList`](../../../iterables/apilist.md)`[`[`LocalVariable`](../../../localvariable/)`]`&#x20;

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

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-10 at 4.02.15 PM.png" alt=""><figcaption></figcaption></figure>
