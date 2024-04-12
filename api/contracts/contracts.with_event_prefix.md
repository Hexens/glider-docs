---
description: >-
  Adds a filter to get contracts that have an event whose name has the given
  prefix.
---

# Contracts.with\_event\_prefix()

## Function Signature

`with_event_prefix(prefix: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_event_prefix("role", sensitivity=False).exec(1)

  return contracts
```

## Output Example

```python
{
    {
        "contract": "0x320d5f8e4d1630d6915c2b676de6aec28a342af8",
        "contract_name": "LibACL"
    }
}
```
