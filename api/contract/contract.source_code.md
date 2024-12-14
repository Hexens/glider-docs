---
description: Returns the source code of the contract.
---

# Contract.source\_code()

`source_code() → str`

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1)

  print(contracts[0].source_code())

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>
