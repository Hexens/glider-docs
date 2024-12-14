---
description: >-
  Adds a filter to get contracts that have at least one function from the given
  names.
---

# Contracts.with\_one\_of\_the\_function\_names()

`with_one_of_the_function_names(names: List[str], sensitivity: bool = True) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_one_of_the_function_names(["deposit", "withdraw"]).exec(1,1)

  functions = contracts.functions().exec()
  for function in functions:
    print(function.name)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
