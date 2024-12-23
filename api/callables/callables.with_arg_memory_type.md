# Callables.with\_arg\_memory\_type()

`with_arg_memory_type(`_`arg_memory_type: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

_`arg_memory_type` can take as arguments: "storage", "memory", "calldata"_

_By default, "memory" is set as the memory type of argument unless stated otherwise explicitly._

Adds a filter to get callables having specified argument memory type. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have a storage argument
  functions = Functions().with_arg_memory_type("storage").exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have a calldata argument
  modifiers = Modifiers().with_arg_memory_type("calldata").exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
