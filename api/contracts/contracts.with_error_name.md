---
description: Adds a filter to get contracts that have an error with the given name.
---

# Contracts.with\_error\_name()

`with_error_name(name: str, sensitivity: boot = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_error_name("Invalid").exec(1)
  errors = contracts[0].errors().exec()
  for error in errors:
    print(error.signature)

  return contracts

```

## Output Example

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
