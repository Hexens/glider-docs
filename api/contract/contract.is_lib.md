---
description: Returns true if the Contract is a library, false otherwise.
---

# Contract.is\_lib()

`is_lib() → bool`

## Example query

```python
from glider import *

def query():
  libs = Contracts().exec(10).filter(lambda x: x.is_lib())

  return libs
```

## Example output

<figure><img src="../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>
