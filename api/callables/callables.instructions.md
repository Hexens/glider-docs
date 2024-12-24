# Callables.instructions()

`instructions() →` [`Instructions`](../instructions/)

Returns the [Instructions](../instructions/) object for the instructions of the callables. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the instructions of a list of functions
  instructions = Functions().instructions().exec(100)

  # Return the first five instructions
  return instructions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the instructions of a list of modifiers
  instructions = Modifiers().instructions().exec(100)

  # Return the first five instructions
  return instructions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
