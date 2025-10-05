---
description: Returns throw instructions of the function/modifier.
---

# Callable.throw\_instructions()

`throw_instructions() →` [`Instructions`](../instructions/)

## Query Example&#x20;

```python
from glider import *


def query():
  functions = Functions().with_name("setTokenExchangeRate").exec(1)

  throw_instructions = []
  for function in functions:
    for instruction in function.throw_instructions().exec():
      # Return the throw instructions for each function
      throw_instructions.append(instruction)

  return throw_instructions
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-25 at 2.12.14 PM.png" alt=""><figcaption></figcaption></figure>

