---
description: Adds a filter to get contracts that are not interface.
---

# Contracts.non\_interface\_contracts()

`non_interface_contracts() ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():

  non_interface_contracts = Contracts().non_interface_contracts().exec(3)

  return non_interface_contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>
