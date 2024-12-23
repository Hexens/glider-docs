---
description: >-
  with_all_properties is deprecated and will be removed in future versions.
  Please use with_properties in- stead. Adds a filter to get functions that have
  all given properties.
---

# Functions.with\_all\_properties()

**Deprecated:** This method is deprecated and will be removed in future versions.

**Alternative:** Use `with_properties()` instead for improved functionality.

`with_all_properties(`_`properties: List[`_[_`MethodProp`_](../methodprop/)_`]`_`) →` [`Functions`](./)

## Example

```python
from glider import *

def query():
  properties = [MethodProp.IS_PAYABLE, MethodProp.EXTERNAL]
  # Fetch a list of functions with all the properties
  functions = Functions().with_all_properties(properties).exec(3)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
