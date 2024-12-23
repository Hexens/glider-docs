# Callables.with\_arg\_types()

`with_arg_types(`_`arg_types: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Callable`](./)

Adds a filter to get callables having specified argument types like "address" or even non-elementary types like structs is strict ordering. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a single argument type, refer to [Callables.with\_arg\_type()](callables.with_arg_type.md).

_Note that the order of the argument types is important. I.e. calling `.with_arg_types(["a", "b"])` is **not equivalent** to calling `.with_arg_types(["b", "a"])` !_

_Note that the function will handle alias types, e.g. if uint256 is passed to the function, the results will also include the alias "uint" variables_

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `uint256` and `address` as argument types
  functions = Functions().with_arg_types(["uint256", "address"]).exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `uint256` and `State` as their argument types
  modifiers = Modifiers().with_arg_types(["uint256", "State"]).exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
