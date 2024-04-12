---
description: Adds a filter to get contracts whose names match the given regex.
---

# Contracts.name\_regex()

## Function Signature

`name_regex(regex: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():

  non_interface_contract = Contracts().name_regex('^[^I][^A-Z].*').exec(1)

  return non_interface_contract
```

## Output Example

```python
{
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
        "contract_name": "Context"
    }
}
```
