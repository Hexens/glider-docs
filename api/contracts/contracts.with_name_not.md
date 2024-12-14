---
description: Adds a filter to get contracts that don't have the given name.
---

# Contracts.with\_name\_not()

`with_name_not(name: str, sensitivity: bool = True) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_name_not("Ownable").exec(10)
  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

