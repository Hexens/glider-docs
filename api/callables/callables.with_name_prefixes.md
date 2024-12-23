# Callables.with\_name\_prefixes()

`with_name_prefixes(`_`prefixes: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables whose names have prefixes from the given list of prefixes. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a single prefix, refer to [Callables.with\_name\_prefix()](callables.with_name_prefix.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `min` or `max` as prefix
  functions = Functions().with_name_prefixes(["min", "max"]).exec(100)

  # Return the first five functions
  return functions[:4]
```

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `before` or `after` as prefix
  modifiers = Modifiers().with_name_prefixes(["before", "after"]).exec(100)

  # Return the first five modifiers
  return modifiers[:4]
```

Output:

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
