---
description: >-
  Adds a filter to get contracts that have at least one function from the given
  names.
---

# Contracts. with\_one\_of\_the\_function\_names()

`with_one_of_the_function_names(names: List[str], sensitivity: bool = True) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts().
    with_one_of_the_function_names(["deposit", "withdraw"]).
    exec(1)
  )

  return contracts
```

## Output Example

```json
{
    {
        "contract": "0x23297ee054e8f600af482013ddbe856b7178a7d3",
        "contract_name": "WETH9"
    }
}
```
