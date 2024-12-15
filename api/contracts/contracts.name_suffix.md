---
description: Adds a filter to get contracts that names have the given suffix.
---

# Contracts.with\_name\_suffix()

`with_name_suffix(`_`suffix: str, sensitivity: bool = True`_`) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():

  prefix_contracts = Contracts().with_name_suffix("link", sensitivity=False).exec(1)

  return prefix_contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>
