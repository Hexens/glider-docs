---
description: >-
  Adds a filter to get contracts that have an event whose name has the given
  suffix.
---

# Contracts.with\_event\_suffix()

`with_event_suffix(suffix: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_event_suffix('validated').exec(1)
  events = contracts[0].events()
  for event in events:
    print(event.signature)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>
