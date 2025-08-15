---
description: Adds a filter to get contracts that are not interface.
---

# Contracts.non\_interface\_contracts()

`non_interface_contracts() →` [`Contracts`](./)

## Query Example

```python
from glider import *


def query():
  non_interface_contracts = Contracts().non_interface_contracts().exec(5)

  return non_interface_contracts
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-14 at 1.29.00 PM.png" alt=""><figcaption></figcaption></figure>
