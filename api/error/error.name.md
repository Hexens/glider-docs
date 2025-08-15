---
description: Returns the name of the error.
---

# Error.name

_`property`_` ``name :`` `_`str`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 2265)

  for contract in contracts:
    for error in contract.errors().exec():
      print(error.name)

  return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-29 at 6.12.43 PM.png" alt=""><figcaption></figcaption></figure>
