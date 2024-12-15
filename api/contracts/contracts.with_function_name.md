---
description: Adds a filter to get contracts that have a function with the given name.
---

# Contracts.with\_function\_name()

`with_function_name(name: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_function_name('receive').exec(1)

  functions = contracts.functions().exec()
  for function in functions:
    print(function.name)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
