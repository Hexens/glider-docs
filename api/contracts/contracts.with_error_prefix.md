---
description: >-
  Adds a filter to get contracts that have an error whose name has the given
  prefix.
---

# Contracts.with\_error\_prefix()

`with_error_prefix(prefix: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Example Query

```python
from glider import *

def query():
  contracts = Contracts().with_error_prefix("Wrong").exec(1)
  errors = contracts[0].errors().exec()
  for error in errors:
    print(error.signature)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
