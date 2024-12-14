---
description: Adds a filter to get contracts that have an event with the given signature.
---

# Contracts.with\_event\_signature()

`with_event_signature(signature: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_event_signature('Deposit(uint256,address)').exec(1)
  events = contracts[0].events()
  for event in events:
    print(event.signature)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>
