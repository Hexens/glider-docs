---
description: >-
  Adds a filter to get contracts that have an error whose name has the given
  prefix.
---

# Contracts.with\_error\_prefix()

`with_error_prefix(prefix: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Example Query

```python
from glider import *

def query():
  contracts = Contracts().with_error_prefix("Wrong").exec(1)

  return contracts
```

## Output Example

```python
{
    {
        "contract": "0x4730c58fda9d78f60c987039aeab7d261aad942e",
        "contract_name": "PrqBridge"
    }
}
```
