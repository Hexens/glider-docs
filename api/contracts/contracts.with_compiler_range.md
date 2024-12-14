---
description: >-
  Adds a filter to get contracts whose compilation version is in the given
  range.
---

# Contracts.with\_compiler\_range()

`with_compiler_range(lower_bound: str, upper_bound: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_compiler_range("0.4.20", "0.4.24").exec(3)

  for contract in contracts:
    print(contract.pragmas())

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
