---
description: The function returns all the events of a Contract.
---

# Contract.events()

`events() →` [`APIList`](../iterables/apilist.md)`[`[`Event`](../event/)`]`

## Example query

```python
from glider import *

def query():
  contracts = Contracts().with_name("IERC721").exec(1)

  for contract in contracts:
    events = contract.events()
    for event in events:
      print(event.signature)

  return contracts
```

## &#x20;Output Example

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
