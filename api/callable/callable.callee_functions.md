---
description: >-
  Returns a Functions object that represents called functions from the
  function/modifier.
---

# Callable.callee\_functions()

`callee_functions() →` [`Functions`](../callables/functions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(30)

  called_functions = []
  for function in functions:
    for called in function.callee_functions().exec():
      # Return each called function from this specific one
      called_functions.append(called)

  return called_functions
```

## Example output

<figure><img src="../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>
