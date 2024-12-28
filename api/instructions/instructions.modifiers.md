# Instructions.modifiers()

**`modifiers`**`() →` [`Modifiers`](../callables/modifiers/)

Returns [Modifiers](../callables/modifiers/) object for the modifiers of the instructions. Note: The function will return parent modifiers for those instructions that belong to a modifier, not to a function. To get parent functions of that instructions use `functions()` method.

## Query Example

```python
from glider import *

def query():

  return Instructions().modifiers().exec(1)
```

## Output Example

<figure><img src="../../.gitbook/assets/image (257).png" alt=""><figcaption></figcaption></figure>
