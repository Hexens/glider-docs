---
description: Returns the list of arguments of the error.
---

# Error.args

_`property`_` ``args:`` `_`List[Dict]`_

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 2265) 

  for contract in contracts:
    for error in contract.errors().exec():
      print(f"{error.name} - {error.args}")

  return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-29 at 6.10.29 PM.png" alt=""><figcaption></figcaption></figure>
