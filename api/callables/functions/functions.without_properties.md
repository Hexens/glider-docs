---
description: >-
  without_properties is deprecated and will be removed in future versions.
  Please use with_properties instead. Adds a filter to get functions that don't
  have any of the given properties.
---

# Functions.without\_properties()

**Deprecated**: This method is deprecated and will be removed in future versions.

**Alternative:** Use `with_properties()` instead for improved functionality.

`without_properties(`_`properties: List[MethodProp]`_`) →` [`Functions`](./)

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions which are not external/public
  functions = Functions().without_properties([MethodProp.EXTERNAL, MethodProp.PUBLIC]).exec(3)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>
