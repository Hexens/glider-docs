# Callables.with\_name\_regex()

`with_name_regex(`_`regex: str`_`) →` [`Callables`](./)

Adds a filter to get callables whose names match the given regex expression. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a list of regex expression, refer to [Callables.with\_name\_regexes()](callables.with_name_regexes.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `claim` in their name but do not start with `_`
  functions = Functions().with_name_regex(r"^(?!_).*claim.*$").exec(100)

  # Return the first five functions
  return functions[:1]
```

Output:

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `claim` in their name but do not start with `only`
  modifiers = Modifiers().with_name_regex(r"^(?!only).*claim.*$").exec(100)

  # Return the first five modifiers
  return modifiers[:3]
```

Output:

<figure><img src="../../.gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>
