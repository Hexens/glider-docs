---
description: Returns the address of the contract.
---

# Contract.address()

`address() → str`

## Example query

```python
from glider import *

def query():
  contracts = Contracts().with_name("Deposit").exec(5)
  
  for contract in contracts:
    print(contract.address())

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>
