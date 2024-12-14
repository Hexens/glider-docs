---
description: Returns true if the Contract is main, false otherwise.
---

# Contract.is\_main()

`is_main() → bool`

The engine marks the contract as main, if it is the one being executed on the deployed address

## Example query

```python
from glider import *

def query():
  mains = Contracts().exec(30).filter(lambda x: x.is_main())

  return mains
```

## Example output

<figure><img src="../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>
