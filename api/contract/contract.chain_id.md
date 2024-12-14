---
description: Returns the ChainID of the blockchain where the Contract was deployed.
---

# Contract.chain\_id()

`chain_id() → int`

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(5)

  for contract in contracts:
    print(contract.chain_id())

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>
