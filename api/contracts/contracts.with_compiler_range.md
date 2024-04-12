---
description: >-
  Adds a filter to get contracts whose compilation version is in the given
  range.
---

# Contracts.with\_compiler\_range()

## Function Signature

`with_compiler_range(lower_bound: str, upper_bound: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_compiler_range("0.4.20", "0.4.24").exec(10)

  return contracts
```

## Output Example

```python
{
    {
        "contract": "0xcb3590c74e77b1ccc0975029bc1bf1e1b69a1edd",
        "contract_name": "SafeMath"
    }
}
```
