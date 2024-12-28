# Functions.without\_modifier\_names()

`without_modifier_names(`_`names: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Functions`](./)

Adds a filter to get functions that don't have any modifier with one of the given names.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions without modifiers from the given list
  functions = Functions().without_modifier_names(['onlyAdmin','onlyOwner']).exec(10)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (9) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
