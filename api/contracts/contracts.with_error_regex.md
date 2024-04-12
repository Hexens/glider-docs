---
description: >-
  Adds a filter to get contracts that have an error whose name matches the given
  regex.
---

# Contracts.with\_error\_regex()

## Function Signature

`with_error_regex(regex: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_error_regex('^Err.*').exec(1)
  
  return contracts
```

## Output Example

```python
{
    {
        "contract": "0x423ce5282c460eed5fe0786b4d47d2c2a4ef3721",
        "contract_name": "IRiverV1"
    }
}
```
