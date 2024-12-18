# Functions.with\_all\_modifier\_names()

`with_all_modifier_names(names: List[str], sensitivity: bool = True) →` [`Functions`](./)

Adds a filter to get functions that have modifiers with all the given names.

## Example

```python
from glider import *

def query():
  functions = Functions().with_all_modifier_names(['lock', 'onlyOwner']).exec(1)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
