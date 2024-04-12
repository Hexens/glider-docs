---
description: Adds a filter to get contracts that have an event with the given name.
---

# Contracts.with\_event\_name()

## Function Signature

`with_event_name(name: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_event_name('Modified').exec(1)

  return contracts
```

## Output Example

```python
{
    {
        "contract": "0x92a6b64544643a70ac3fbb825524a3138c4cac57",
        "contract_name": "IDCAHubPositionHandler"

    }
}
```
