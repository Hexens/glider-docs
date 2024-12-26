# Callables.without\_name()

`without_name(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables that don't have the specified name. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To get the callables with a specified name, refer to [Callables.with\_name()](callables.with_name.md).

To filter given a list of undesired names, refer to [Callables.without\_names()](callables.without_names.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions that are not named `distributeFunds`
  functions = Functions().without_name("distributeFunds").exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that are not named `onlyCaller`
  modifiers = Modifiers().without_name("onlyCaller").exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
