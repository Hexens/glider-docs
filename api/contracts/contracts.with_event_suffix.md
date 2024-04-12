---
description: >-
  Adds a filter to get contracts that have an event whose name has the given
  suffix.
---

# Contracts.with\_event\_suffix()

## Function Signature

`with_event_suffix(suffix: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_event_suffix('validated').exec(1)
  
  return contracts
```

## Output Example

```python
{
    {
        "contract": "0x5eeda8c2a8b22177abd18ebf9382f8eb0ce232d3",
        "contract_name": "NFTMarket"

    }
}
```
