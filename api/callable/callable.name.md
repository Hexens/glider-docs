---
description: Returns the function's or modifier's name.
---

# Callable.name

`property: name -> str`

## Example

```python
from glider import *
def query():
  contracts = Contracts().exec(1)

  contracts_with_callables = []
  for c in contracts:
    for function in c.functions().exec():
      print(f"contract name: {c.name} | function name: {function.name}")

    for modifier in c.modifiers().list():
      print(f"contract name: {c.name} | function name: {modifier.name}")

  return contracts
```

## Example output

<figure><img src="../../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>
