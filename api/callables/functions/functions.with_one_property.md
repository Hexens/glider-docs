---
description: >-
  with_one_property is deprecated and will be removed in future versions. Please
  use with_properties in- stead. Adds a filter to get functions that at least
  have one of the given properties.
---

# Functions.with\_one\_property()

**Deprecated:** This method is deprecated and will be removed in future versions.

**Alternative:** Use `with_properties()` instead for improved functionality.

`with_one_property(`_`properties: List[`_[_`MethodProp`_](../methodprop/)_`]`_`) →` [`Functions`](./)

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions which a external
  functions = Functions().with_one_property([MethodProp.EXTERNAL]).exec(3, 100)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (11) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
