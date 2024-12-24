# Callables.with\_one\_of\_the\_names()

`with_one_of_the_names(`_`names: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables having specified names. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a single name, refer to [Callables.with\_name()](callables.with_name.md).

To get all but some specified names, refer to [Callables.without\_names()](callables.without_names.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions that are named `sendMessage` and `totalSupply`
  functions = Functions().with_one_of_the_names(["sendMessage", "totalSupply"]).exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that are named `onlyCaller` and `onlyClient`
  modifiers = Modifiers().with_one_of_the_names(["onlyCaller", "onlyClient"]).exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>
