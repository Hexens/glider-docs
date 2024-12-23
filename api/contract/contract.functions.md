---
description: Returns all the functions of a Contract.
---

# Contract.functions()

`functions() →` [`Functions`](../callables/functions/)

The function returns all of the functions that the Contract has, including the inherited functions from its base classes.

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1)

  for contract in contracts:
    functions = contract.functions().exec()
    for function in functions:
      print(function.name)

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
