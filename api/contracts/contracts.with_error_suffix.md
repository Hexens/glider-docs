---
description: >-
  Adds a filter to get contracts that have an error whose name has the given
  suffix.
---

# Contracts.with\_error\_suffix()

`with_error_suffix(suffix: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_error_suffix("admin", sensitivity=False).exec(1)
  errors = contracts[0].errors().exec()
  for error in errors:
    print(error.signature)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>
