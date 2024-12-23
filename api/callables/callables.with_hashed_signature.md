# Callables.with\_hashed\_signature()

`with_hashed_signature(`_`signature_hash: int`_`) →` [`Callables`](./)

Adds a filter to get callables having specified selector (4 bytes of signature hash). Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have 0x70a08231 as selector
  functions = Functions().with_hashed_signature(0x70a08231).exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have 0x2ddb862d as their selector
  modifiers = Modifiers().with_hashed_signature(0x2ddb862d).exec(100)

  # Return the first five modifiers
  return modifiers[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (177).png" alt=""><figcaption></figcaption></figure>
