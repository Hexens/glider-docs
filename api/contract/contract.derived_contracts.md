---
description: >-
  Returns Contracts object for the contracts which were derived from the
  contract.
---

# Contract.derived\_contracts()

`derived_contracts() →` [`Contracts`](../contracts/)

## Example query

```python
from glider import *


def query():
  contracts = Contracts().exec(1)
  
  for contract in contracts:
    derived_contracts = contract.derived_contracts().exec()
    print(f"Contract name: {contract.name}")
    for derived_contract in derived_contracts:
      print(f"Derived contract name: {derived_contract.name}")
 
  return []
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-24 at 11.46.45 AM.png" alt=""><figcaption></figcaption></figure>
