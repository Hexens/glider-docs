---
description: Adds a filter to get contracts that have an error with the given signature.
---

# Contracts.with\_error\_signature()

`with_error_signature(signature: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_error_signature('InsufficientBalance(uint256,uint256)').exec(1)
  errors = contracts[0].errors().exec()
  for error in errors:
    print(error.signature)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
