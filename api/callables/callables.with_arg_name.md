# Callables.with\_arg\_name()

`with_arg_name(`_`arg_name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables having specified argument name. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `_address` as one of their arguments
  functions = Functions().with_arg_name("_address").exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `_caller` as one of their arguments
  modifiers = Modifiers().with_arg_name("_caller").exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
