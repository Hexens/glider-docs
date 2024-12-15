---
description: Returns the Modifiers object for the modifiers of the function.
---

# Function.modifiers()

`modifiers() →` [`Modifiers`](../../callables/modifiers/)

Returns the [Modifiers](../../callables/modifiers/) object for the modifiers of the function.

## Example

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().with_one_property([MethodProp.HAS_MODIFIERS]).exec(1)

  # Retrieve the modifiers of the first function
  modifers = functions[0].modifiers().exec()

  return modifers
```

## Output

<figure><img src="../../../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>
