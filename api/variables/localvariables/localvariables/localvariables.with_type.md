---
description: Returns the list of local variables having specified type.
---

# LocalVariables.with\_type()

`with_type(var_type: str) →` [`APIList`](../../../iterables/apilist.md)`[`[`LocalVariable`](../localvariable/)`]`



## Query Example

```python
from glider import *

def query():

  local_variables = (
    Functions()
    .exec(1, 17)
    .local_variables()
    )

  print(local_variables[0].with_type("address").source_code())

  return []
```

## Output Example&#x20;

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
