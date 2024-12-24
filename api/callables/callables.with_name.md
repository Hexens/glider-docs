# Callables.with\_name()

`with_name(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables having specified name. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To get all but the specified name, refer to [Callables.without\_name()](callables.without_name.md).

To filter given a list of names, refer to [Callables.with\_one\_of\_the\_names()](callables.with_one_of_the_names.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions named `distributeFunds`
  functions = Functions().with_name("distributeFunds").exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers named `onlyCaller`
  modifiers = Modifiers().with_name("onlyCaller").exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
