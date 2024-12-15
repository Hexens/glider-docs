---
description: Adds a filter to get contracts whose names have the given prefix.
---

# Contracts.with\_name\_prefix()

`with_name_prefix(`_`prefix: str, sensitivity: bool = True`_`) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():

  main_contracts = Contracts().with_name_prefix("Acc", sensitivity=True).exec(5)

  return main_contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>
