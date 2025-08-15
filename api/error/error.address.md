---
description: Returns the address of the error.
---

# Error.address

_`property`_` ``address:`` `_`str`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 2265) 

  for contract in contracts:
    for error in contract.errors().exec():
      print(f"{error.name} - {error.address}")

  return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-14 at 1.43.29 PM.png" alt=""><figcaption></figcaption></figure>
