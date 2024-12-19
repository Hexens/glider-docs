---
description: Returns Contracts object for the contracts of the functions/modifiers.
---

# Callables.contracts()

`contracts() →` [`Contracts`](../contracts/)

Returns the [Contracts](../contracts/) object for the contracts of the callables. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

The function will account for the inheritance of the contracts, thus, even one callable can have multiple contracts where it is accessible.

### Functions Example

```python
from glider import *

def query():
  # Retrieve the contracts of a list of functions
  contracts = Functions().contracts().exec(100)

  # Return the first five contracts
  return contracts[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (139).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the contracts of a list of modifiers
  contracts = Modifiers().contracts().exec(100)

  # Return the first five contracts
  return contracts[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (141).png" alt=""><figcaption></figcaption></figure>
