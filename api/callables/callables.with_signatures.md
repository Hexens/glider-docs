# Callables.with\_signatures()

`with_signatures(`_`signatures: List[str]`_`) →` [`Callables`](./)

Adds a filter to get callables that have any of the given signatures. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a single signature, refer to [Callables.with\_signature()](callables.with_signature.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions that have `approve(address)` or `claim(address,uint256)` as signatures
  functions = Functions() \
      .with_signatures([
          "approve(address)",
          "claim(address,uint256)"
      ]) \
      .exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve all the modifiers that have `nonReentrant()` or `initializer()` as their signatures
  modifiers = Modifiers() \
    .with_signatures([
      "nonReentrant()",
      "initializer()"
    ]) \
    .exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
