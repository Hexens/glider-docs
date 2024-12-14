---
description: Returns all the modifiers of a Contract.
---

# Contract.modifiers()

`modifiers() →` [`Modifiers`](../callables/modifiers/)

The function also handles inherited modifiers.

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1,1)

  for contract in contracts:
    modifiers = contract.modifiers().exec()
    for modifier in modifiers:
      print(modifier.name)

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>
