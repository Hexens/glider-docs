---
description: The function returns all the enums of a Contract.
---

# Contract.enums()

`enums() →` [`APIList`](../iterables/apilist.md)`[`[`Enums`](../enums/)`]`

## Example query

```python
python
from glider import *

def query():
  contracts = Contracts().with_name("Math").exec(1)

  for contract in contracts:
    enums = contract.enums().exec()
    for enum in enums:
      print(enum.name)
      print(enum.values)

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
