---
description: Returns the list of all pragmas of the contract.
---

# Contract.pragmas()

`pragmas() → List[Tuple[str, str]]`

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(5)

  for contract in contracts:
    print(contract.pragmas())


  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>
