---
description: Returns the modifier's properties.
---

# Modifier.properties()

`properties() →` [`APIList`](../iterables/apilist.md)`[`[`MethodProps`](../callables/methodprop/)`]`

## Query Example

```python
from glider import *

def query():
  # Fetch a list of modifiers
  modifiers = Modifiers().exec(1)

  # Retrieve the properties of the first modifier
  properties = modifiers[0].properties()
  for prop in properties:
    print(prop)

  return modifiers
```

## Output Example

<figure><img src="../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>
