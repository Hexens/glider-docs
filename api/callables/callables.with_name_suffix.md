# Callables.with\_name\_suffix()

`with_name_suffix(`_`suffix: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables whose names have the given suffix. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a list of suffixes, refer to [Callables.with\_name\_suffixes()](callables.with_name_suffixes.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `down` as suffix
  functions = Functions().with_name_suffix("down").exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (166).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `Initialized` as suffix
  modifiers = Modifiers().with_name_suffix("Initialized").exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (168).png" alt=""><figcaption></figcaption></figure>
