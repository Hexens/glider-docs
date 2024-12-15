---
description: Returns a Functions object that represents functions that call the function.
---

# Function.caller\_functions()

`caller_functions() →` [`Functions`](../../callables/functions/)

The caller functions are the functions that directly call the specified function.

## Example

```python
from glider import *

def query():
  # Retrieve a function with name _afterTokenTransfer
  functions = Functions().with_name('_afterTokenTransfer').exec(1)

  # Return its caller functions
  return functions[0].caller_functions().exec()
```

## Output

<figure><img src="../../../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>



