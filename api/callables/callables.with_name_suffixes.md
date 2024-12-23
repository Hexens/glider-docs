# Callables.with\_name\_suffixes()

`with_name_suffixes(`_`suffixes: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables whose names have suffixes from the given list of suffixes. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a single prefix, refer to [Callables.with\_name\_suffix()](callables.with_name_suffix.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `Flashloan` or `cast` as suffix
  functions = Functions().with_name_suffixes(["Flashloan", "cast"]).exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (169).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `Initialized` or `Open` as suffix
  modifiers = Modifiers().with_name_suffixes(["Initialized", "Open"]).exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (171).png" alt=""><figcaption></figcaption></figure>
