---
description: Adds a filter to get contracts that are interface.
---

# Contracts.interface\_contracts()

`interface_contracts() →` [`Contracts`](../contract/)

## Example Query

```python
from glider import *

def query():

  interface = Contracts().interface_contracts().exec(1)

  return interface
```

## Output Example

<figure><img src="../../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>
