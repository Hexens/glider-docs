---
description: Returns the function's properties.
---

# Function.properties()

`properties() →` [`APIList`](../../iterables/apilist.md)`[`[`MethodProp`](../../callables/methodprop/)`]`

Returns the function's properties as an [APIList](../../iterables/apilist.md) of [MethodProps](../../callables/methodprop/).

## Example

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(1)

  # Retrieve the properties of the first function
  properties = functions[0].properties()
  for prop in properties:
    print(prop)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>
