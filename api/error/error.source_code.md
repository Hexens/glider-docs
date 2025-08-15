---
description: Returns the source code of the error.
---

# Error.source\_code()

`source_code() → str`

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 2265)

  for contract in contracts:
    for error in contract.errors().exec():
      print(error.source_code())

  return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-29 at 6.19.02 PM.png" alt=""><figcaption></figcaption></figure>
