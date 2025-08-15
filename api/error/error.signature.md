---
description: Returns the signature of the error.
---

# Error.signature

_`property`_` ``signature :`` `_`str`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 2265)

  for contract in contracts:
    for error in contract.errors().exec():
      print(error.signature)

  return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-29 at 6.13.30 PM.png" alt=""><figcaption></figcaption></figure>
