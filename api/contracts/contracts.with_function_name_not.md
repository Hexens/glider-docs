---
description: >-
  Adds a filter to get contracts that don't have any function with the given
  name.
---

# Contracts.with\_function\_name\_not()

## Function Signature

`with_function_name_not(name: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_function_name_not('transfer').exec(1)

  return contracts
```

## Output Example

```python
{
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "Context"
    }
}
```
