# Functions.with\_modifier\_name\_regex()

`with_modifier_name_regex(`_`regex: str`_`) →` [`Functions`](./)

Adds a filter to get functions, that have modifier whose name matches the given regex.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions with modifiers starting with 'only'
  functions = Functions().with_modifier_name_regex('^only.*').exec(3)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>
