---
description: >-
  Returns Contracts object for the contracts from which the contract was
  inherited directly.
---

# Contract.parent\_contracts()

`parent_contracts() →` [`Contracts`](../contracts/)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1,1)

  for contract in contracts:
    parent_contracts = contract.parent_contracts().exec()
    for parent_contract in parent_contracts:
      print(parent_contract.name)

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>
