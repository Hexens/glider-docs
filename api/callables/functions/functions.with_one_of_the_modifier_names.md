# Functions.with\_one\_of\_the\_modifier\_names()

`with_one_of_the_modifier_names(`_`names: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Functions`](./)

Adds a filter to get functions that have a modifier with one of the given names.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions with modifiers from the given list
  functions = Functions().with_one_of_the_modifier_names(['onlyAdmin','onlyOwner']).exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (8) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
