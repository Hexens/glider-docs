---
description: Returns the list of local variables having specified type.
---

# LocalVariables.with\_type()

`with_type(var_type: str) →` [`APIList`](../../../iterables/apilist.md)`[`[`LocalVariable`](../localvariable/)`]`

## Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_name("purchaseDataset")
    .exec(1)
  )

  for func in functions:
    local_vars = func.local_variables().with_type("address")
    for local_var in local_vars:
      print(local_var.source_code())

  return functions
```

## Example Output

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-10 at 3.57.27 PM.png" alt=""><figcaption></figcaption></figure>
