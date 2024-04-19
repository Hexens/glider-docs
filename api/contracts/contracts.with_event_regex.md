---
description: >-
  Adds a filter to get contracts that have an event whose name matches the given
  regex.
---

# Contracts.with\_event\_regex()

`with_event_regex(regex: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_event_regex('^change.*').exec(1)

  return contracts
```

## Output Example

```python
{
    {
        "contract": "0xf7ee2cea69f9013098abc8ba63844a228885da4c",
        "contract_name": "VaultFactory"
    }
}
```
