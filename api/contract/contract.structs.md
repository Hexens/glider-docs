---
description: Returns the list of all structs of the contract.
---

# Contract.structs()

`structs() →` [`Structs`](../structs/)

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 20)

  for contract in contracts:
    structs = contract.structs().exec()
    for struct in structs:
      print(struct.name)

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>
