---
description: Adds a filter to get contracts with the given name.
---

# Contracts.with\_name()

`with_name(name: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_name("Manager").exec(10)
  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>
