---
description: Adds a filter to get contracts that have functions with all the given names.
---

# Contracts.with\_all\_function\_names()

`with_all_function_names(names: List[str], sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts().
    non_interface_contracts().
    with_all_function_names(["transfer", "TransferFrom"], sensitivity=False).
    exec(1))

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>
