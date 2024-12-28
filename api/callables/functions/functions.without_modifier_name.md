# Functions.without\_modifier\_name()

`without_modifier_name(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Functions`](./)

Adds a filter to get functions that either have no modifier with the given name or have no modifier at all.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions without onlyOwner modifier
  functions = Functions().without_modifier_name('onlyOwner').exec(3)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
