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
    .exec(1, 50)
    )

  for func in functions:
    local_vars = func.local_variables().with_memory_type("memory")
    print(local_vars[0].source_code())

  return functions
```

## Output Example

<figure><img src="../../../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

