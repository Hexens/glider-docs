# Callables.with\_arg\_type()

`with_arg_type(`_`arg_type: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables having specified argument type like "address" or even non-elementary types like structs. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a list of argument types, refer to [Callables.with\_arg\_types()](callables.with_arg_types.md).

_Note that the function will handle alias types, e.g. if uint256 is passed to the function, the results will also include the alias "uint" variables_

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `Order` as one of their argument types
  functions = Functions().with_arg_type("Order").exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (175).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `Set` as one of their argument types
  modifiers = Modifiers().with_arg_type("State").exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (176).png" alt=""><figcaption></figcaption></figure>
