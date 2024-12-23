---
description: Adds a filter to get contracts that are main.
---

# Contracts.mains()

`mains() →` [`Contracts`](./)

The engine marks the contract as main, that is the one being executed on the deployed address

## Query Example

```python
from glider import *

def query():

  main_contracts = Contracts().mains().exec(5)

  return main_contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (8) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
