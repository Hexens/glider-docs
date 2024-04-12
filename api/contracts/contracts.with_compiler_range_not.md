---
description: >-
  Adds a filter to get contracts whose compilation version isn't in the given
  range.
---

# Contracts.with\_compiler\_range\_not()

## Function Signature

`with_compiler_range_not(lower_bound: str, upper_bound: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts().
    non_interface_contracts().
    with_compiler_range_not("0.5.0", "0.5.17").
    exec(1))

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
