---
description: >-
  Adds a filter to get contracts that have an error whose name has the given
  suffix.
---

# Contracts.with\_error\_suffix()

## Function Signature

`with_error_suffix(suffix: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_error_suffix("admin", sensitivity=False).exec(1)

  return contracts
```

## Output Example

```python
{
    {
        "contract": "0xe941bd60bd0c92605f8d90992c7dce3c5fc229f3",
        "contract_name": "IErrors",
    }
}
```
