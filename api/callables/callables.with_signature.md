# Callables.with\_signature()

`with_signature(`_`signature: str`_`) →` [`Callables`](./)

Adds a filter to get callables that have the given signature. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a list of signatures, refer to [Callables.with\_signatures()](callables.with_signatures.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions with the signature `transferFrom(address,address,uint256)`
  functions = Functions().with_signature("transferFrom(address,address,uint256)").exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (8) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve all the modifiers with the signature `nonReentrant()`
  modifiers = Modifiers().with_signature("nonReentrant()").exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (10) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
