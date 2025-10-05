---
description: Returns try instructions of the function/modifier.
---

# Callable.try\_instructions()

`try_instructions() →` [`Instructions`](../instructions/)

## Query Example

```python
from glider import *


def query():
  functions = Functions().with_name("processFee").exec(1)

  try_instructions = []
  for function in functions:
    for instruction in function.try_instructions().exec():
      # Return the try instructions for each function
      try_instructions.append(instruction)

  return try_instructions
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-25 at 3.42.31 PM.png" alt=""><figcaption></figcaption></figure>
