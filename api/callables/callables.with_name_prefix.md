# Callables.with\_name\_prefix()

`with_name_prefix(`_`prefix: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables whose names have the given prefix. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a list of prefixes, refer to [Callables.with\_name\_prefixes()](callables.with_name_prefixes.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `min` as prefix
  functions = Functions().with_name_prefix("min").exec(100)

  # Return the first five functions
  return functions[:4]
```

Output:

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `only` as prefix
  modifiers = Modifiers().with_name_prefix("only").exec(100)

  # Return the first five modifiers
  return modifiers[:4]
```

Output:

<figure><img src="../../.gitbook/assets/image (160).png" alt=""><figcaption></figcaption></figure>
