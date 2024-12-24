# Functions.with\_one\_of\_the\_modifier\_name\_regexes()

`with_one_of_the_modifier_name_regexes(`_`regexes: List[str]`_`) →` [`Functions`](./)

Adds a filter to get functions that have a modifier whose name matches one of the given regexes.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions with modifiers matching regex list
  functions = Functions().with_one_of_the_modifier_name_regexes(['^only.*', 'admin']).exec(10)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (10) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
