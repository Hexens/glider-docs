---
description: Returns the name of a Contract.
---

# Contract.name

_`property`_` ``name`_`: str`_

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(5)

  for contract in contracts:
    print(contract.name)

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>
