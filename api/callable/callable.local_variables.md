---
description: >-
  Returns a LocalVariables object for the local variables of the
  function/modifier.
---

# Callable.local\_variables()

`local_variables() →` [`LocalVariables`](../localvariables/)

## Query Example

```python
from glider import *

def query():
    functions = Functions().exec(1, 100)

    for function in functions:
        for local_var in function.local_variables().list():
            print(local_var.name)

    return functions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (134).png" alt=""><figcaption></figcaption></figure>
