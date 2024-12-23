---
description: The function returns all the errors of a Contract.
---

# Contract.errors()

`errors() →` [`Errors`](../errors/)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 13)

  for contract in contracts:
    errors = contract.errors().exec()
    for error in errors:
      print(error.signature)

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
