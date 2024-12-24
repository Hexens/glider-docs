# Callables.without\_names()

`without_names(`_`names: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables that that don't have the specified names. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To get the callables without a specified name, refer to [Callables.without\_name()](callables.without_name.md).

To filter given a list of names, refer to [Callables.with\_one\_of\_the\_names()](callables.with_one_of_the_names.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions that are not named `_msgSender` and `_msgData`
  functions = Functions().without_names(["_msgSender", "_msgData"]).exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that are not named `onlyOwner` and `onlyMinter`
  modifiers = Modifiers().without_names(["onlyOwner", "onlyMinter"]).exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>
