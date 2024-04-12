---
description: >-
  Adds a filter to get contracts that have an event whose name has the given
  prefix.
---

# Contracts.with\_event\_prefix()

## Function Signature

`with_error_suffix(suffix: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_error_prefix("admin", sensitivity=False).exec(1)

  return contracts
```

## Output Example

```python
{
    "contract": "0x83a41749667ba2c944a7ba4f6287d0652bc440f9",
    "contract_name": "ERC721Drop"
}
```
