# Functions.with\_modifier\_signature()

`with_modifier_signature(`_`signature: str`_`) →` [`Functions`](./)

Adds a filter to get functions that have a modifier with the given signature.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions with specific modifier signature
  functions = Functions().with_modifier_signature('onlyOwner(address)').exec(2)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
