# Functions.with\_modifier\_name()

`with_modifier_name(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Functions`](./)

Adds a filter to get functions that have a modifier with the given name.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions with nonReentrant modifier
  functions = Functions().with_modifier_name('nonReentrant').exec(2)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
