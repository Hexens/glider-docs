# Functions.without\_modifiers()

`without_modifiers() →` [`Functions`](./)

Adds a filter to get functions that don't have modifiers at all.

## Example

```python
from glider import *

def query():
  functions = Functions().without_modifiers().exec(1)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
