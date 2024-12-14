---
description: >-
  Adds a filter to get contracts that have an error whose name matches the given
  regex.
---

# Contracts.with\_error\_regex()

`with_error_regex(regex: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_error_regex('^Err.*').exec(1)
  errors = contracts[0].errors().exec()
  for error in errors:
    print(error.signature)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>
