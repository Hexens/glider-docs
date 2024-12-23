# Callables.with\_arg\_count()

`with_arg_count(`_`arg_count: int`_`) →` [`Callables`](./)

Adds a filter to get callables having specified argument count. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have 12 arguments
  functions = Functions().with_arg_count(12).exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have 5 arguments
  modifiers = Modifiers().with_arg_count(5).exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (173).png" alt=""><figcaption></figcaption></figure>
