---
description: >-
  Adds a filter to get contracts whose compilation version isn't in the given
  range.
---

# Contracts.with\_compiler\_range\_not()

`with_compiler_range_not(lower_bound: str, upper_bound: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_compiler_range_not("0.8.0", "0.8.11").exec(3)

  for contract in contracts:
    print(contract.pragmas())

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>
