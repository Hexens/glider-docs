---
description: Adds a filter to get contracts that have an event with the given signature.
---

# Contracts.with\_event\_signature()

`with_event_signature(signature: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts().
    with_event_signature('Deposit(uint256,address)').
    exec(1)
  )

  return contracts
```

## Output Example

```python
{
    {
        "contract": "0xdb5f028d12d703ba79fa00769219853e323685ae",
        "contract_name": "PoHwhale"
    }
}
```
