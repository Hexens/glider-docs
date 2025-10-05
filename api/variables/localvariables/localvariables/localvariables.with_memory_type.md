---
description: Returns the list of local variables having specified memory type.
---

# LocalVariables.with\_memory\_type()

`with_memory_type(memory_type: str) →` [`APIList`](../../../iterables/apilist.md)`[`[`LocalVariable`](../localvariable/)`]`

## Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_name("functionCallWithValue")
    .exec(3)
  )

  for func in functions:
    local_vars = func.local_variables().with_memory_type("memory")
    for local_var in local_vars:
      print(local_var.source_code())

  return functions
```

## Example Output

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-10 at 3.51.37 PM.png" alt=""><figcaption></figcaption></figure>
