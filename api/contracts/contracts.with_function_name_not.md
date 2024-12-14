---
description: >-
  Adds a filter to get contracts that don't have any function with the given
  name.
---

# Contracts.with\_function\_name\_not()

`with_function_name_not(name: str, sensitivity: bool = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_function_name_not('transfer').exec(1,1)

  functions = contracts.functions().exec()
  for function in functions:
    print(function.name)

  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>
