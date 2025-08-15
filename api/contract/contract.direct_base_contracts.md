---
description: >-
  Returns Contracts for the contracts from which the contract was inherited
  directly.
---

# Contract.direct\_base\_contracts()

`direct_base_contracts() →` [`Contracts`](../contracts/) `| NoneObject`

## Query Example

```python
from glider import *


def query():
  contracts = Contracts().exec(1, 7)
  
  for contract in contracts:
    direct_base_contracts = contract.direct_base_contracts().exec()
    print(f"Contract name: {contract.name}")
    for direct_base_contract in direct_base_contracts:
      print(f"Direct base contract name: {direct_base_contracts.name}")
 
  return contracts
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-24 at 11.55.41 AM (1).png" alt=""><figcaption></figcaption></figure>
