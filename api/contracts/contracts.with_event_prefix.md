---
description: >-
  Adds a filter to get contracts that have an event whose name has the given
  prefix.
---

# Contracts.with\_event\_prefix()

`with_event_prefix(prefix: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_event_prefix("role", sensitivity=False).exec(1)
  events = contracts[0].events()
  for event in events:
    print(event.signature)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>
